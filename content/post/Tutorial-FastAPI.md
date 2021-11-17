---
title: "Tutorial FastAPI"
date: 2021-11-13T10:55:19+02:00
draft: false
---

# Um guia para criar API de um jeito rápido

Com uma API podemos criar sistemas melhores e minimizar o entendimento deles.
Através do reuso também podemos nos concentrar no mais importante: A lógica
da aplicação. dessa forma, podemos reutilizar frameworks e bibliotecas construidas
por terceiros.

Neste post, vou apresentar FastAPI: Uma estrutura baseada em python para criar APIs Rest.
Apresentarei brevemente alguns recursos básicos dessa estrutura e, em seguida, criaremos um conjunto de APIs para um sistema de gerenciamento de biblioteca. Conhecimento de python é muito necessário para usar este framework.

Ao final, você será capaz de começar a criar APIs da web prontas para produção e terá o conhecimento necessário para se aprofundar e aprender mais para seus casos de uso específicos.

# 1. O que é a estrutura FastAPI?

FastAPI é uma estrutura da web moderna e de alto desempenho para construção de APIs com Python com base em dicas de tipo padrão. Possui os seguintes recursos princípais:

- **Rápido para executar**: Oferece um desempenho muito alto, a par com NodeJS e Go, graças a Starlette e pydantic.

- **Rápido para codificar** : permite aumentos significativos na velocidade de desenvolvimento.
- **Número reduzido de bugs** : reduz a possibilidade de erros induzidos por humanos.
- **Intuitivo** : oferece ótimo suporte ao editor, com conclusão em qualquer lugar e menos tempo de depuração
- **Simples** : é projetado para ser simples de usar e aprender, para que você gaste menos tempo lendo a documentação.
- **Curto** : minimiza a duplicação de código.
- **Robusto** : fornece código pronto para produção com documentação interativa automática.
- **Baseados em padrões** : É baseado em padrões abertos para APIs, AbraAPI e JSON Schema .

A estrutura é projetada para otimizar sua experiência de desenvolvedor para que você possa escrever um código simples para construir APIs prontas para produção com as melhores práticas por padrão.

### Instalação e configuração

Como em qualquer outro projeto Python, seria melhor começar criando um ambiente virtual. 

````Code
    pip instal pipenv
````
Uma vez instalado, você pode ativar o ambiente virtual executando o comando pipenv shell.

Primeiro, instalaremos o **FastAPI** execuntando o seguinte comando: 

````Code
    pipenv install fastapi
````
> [!Observe]
> O pipenv, não é pip. Quando você estiver no shell, estará usando pipenv.  Subjacente está usando pip, mas todas as entradas estão sendo armazenadas em Pipfile.

OK, então configuramos nosso ambiente de desenvolvimento. É hora de começar a escrever nosso primeiro endpoint de API. Vou criar um arquivo chamado main.py. Este será o ponto de entrada do nosso aplicativo. 

[![main.png](https://i.postimg.cc/CK98hvfT/main.png)](https://postimg.cc/hJbvM1rp)

Se tentarmos executar o programa usando o procedimento normal, você verá que não terá nenhuma resposta. Bem, o FastAPI vem com o **uvicorn** que é um servidor ASGI. Você simplesmente executará o comando:

````code
    uvicorn main:app --reload
````
A linha destacada na saída mostra a URL onde seu aplicativo está sendo servido em sua máquina local. Como você usou --reload para desenvolvimento, ao atualizar o código do aplicativo, o servidor será recarregado automaticamente.

### **Verifique sua resposta**

Abra seu navegador em http://127.0.0.1:8000, o que fará com que ele envie uma solicitação ao seu aplicativo. Em seguida, ele enviará uma resposta JSON com o seguinte:

````Json
    {"Mensagem": "Olá Mundo"}
````
Essa mensagem JSON é o mesmo dicionário que você retornou da função em seu aplicativo. FastAPI se encarrega de serializar o Pythondict em um objeto JSON e definir o apropriado Content-Type.

### Verifique a documentação da API interativa

Agora abra http://127.0.0.1:8000/docs no seu navegador.

Você verá a documentação da API interativa automática fornecida pelo Swagger UI :

[![swagger.png](https://i.postimg.cc/QdKqKVMh/swagger.png)](https://postimg.cc/QFs7R85y)

Caso você precise de algo chique, visite http://localhost:8080/redoc

[![image.png](https://i.postimg.cc/Y9vXR8rL/image.png)](https://postimg.cc/qhdXMsCp)

Como a FastAPI é baseada em padrões como OpenAPI, existem muitas maneiras alternativas de mostrar a documentação da API. FastAPI fornece essas duas alternativas por padrão.

O FastAPI também fornece uma versão OpenAPI de endpoints de API, como este http://127.0.0.1:8000/openapi.json

### Caminho e parâmetros

Suponhamos que queiramos buscar detalhes do livro através de um ID, nós podemos adicionar outro endpoint da API.
Você pode declar **parâmetros** ou **variáveis** de caminho com a mesma sintaxe usada por strings formatadas em python:

````python3
#main.py

from fastapi import FastAPI

app = FastAPI()

@app.get('/livro/{livro_id}')
def detalhes_livro(livro_id):
    return{'livro_id': livro_id}

````

O valor do parâmetro livro_id será passado para a função como argumento livro_id.

Portanto, se você executar este exemplo e for para http://127.0.0.1:8000/livro/1, verá esta resposta:

````json

    {"livro_id": "1"}

````

A resposta contém 1, que é o que foi passado no livro_id! Parâmetro de caminho e depois retornando em um dicionário.

### Parâmetros de caminho com tipos

Você pode declarar o tipo de um parâmetro de caminho na função usando tipos de dados do python:

````python3

    from fastapi import FastAPI

    app = FastAPI()
    @app.get("/livro/{livro_id}")
    def detalhes_livro(livro_id: int):
        return{'livro_id': livro_id}
````

Nesse caso, você declara o livro_id como um tipo int.

Declarar o tipo de um parâmetro de caminho fornecerá suporte ao editor dentro de sua função, com verificações de erro, conclusão e assim por diante.

Agora, se você passar uma string em vez de um inteiro? você terá o seguinte erro:
exemplo, http://127.0.0.1:8000/livro/atomichabit

````json
    {"detail":[{"loc":["path","livro_id"],"msg":"value is not a valid integer","type":"type_error.integer"}]}
````

Ele retornou uma mensagem de erro informando que você enviou o tipo de dados incorreto. Você não precisa escrever um validador para essas coisas mesquinhas. Essa é a beleza de trabalhar na FastAPI.

### String de consulta

E se você passar dados extras na forma de strings de consulta? Por exemplo, seu ponto final de API retorna muitos registros, portanto, você precisa de paginação. Bem, sem problemas, você também pode buscar essas informações.

Primeiro vamos importar o **Optional**.

````python
from fastapi import FastAPI
from typing import Optional 

app = FastAPI()
@app.get("/livro/{livro_id}")
def detalhes_livro(livro_id: int, page: Optional[int] = 1):
    if page:
        return {'livro_id': livro_id, 'page': page}
    return{'livro_id': livro_id}
````

Acesse a URL http://127.0.0.1:8000/livro/1?page=3 e você verá algo como:

````json
    {"livro_id":1,"page":3}
````

Tente com outros números...

Maravilhoso, não?

Até agora,  apenas retornamos manualmente o dict. Não é legal. É bastante comum que você insira um único valor e retorne uma estrutura YUUGE JSON. FastAPI oferece uma maneira elegante de lidar com isso, usando modelos Pydantic.

Os modelos Pydantic realmente ajudam na validação de dados, o que isso significa? Significa que garante que os dados que estão sendo passados ​​são válidos, caso contrário, retorna um erro. Já estamos usando dicas de tipo do Python e esses modelos de dados fazem com que os dados limpos sejam passados. Vamos escrever um pouco de código, vamos criar a nossa API de biblioteca.

````python
#main

from fastapi import FastAPI
# Optional
from typing import Optional
# pydantic
from pydantic import BaseModel

app = FastAPI()

           
class Livros(BaseModel):
    # Criado atributos do livro
    id_livro : int
    titulo : str
    autor : str
    lancamento : int

@app.post('/livros')
async def add_livro(livros: Livros):
    return livros
````

Vá para http://localhost:8080/docse você verá algo como abaixo

[![image.png](https://i.postimg.cc/Dy2Ht9c1/image.png)](https://postimg.cc/4nSWcFq3)

Como esperado, ele apenas retornou o Livros objecto no formato JSON.

A maravilha da documentação do FastAPI não termina aqui, ela também permite que você defina a estrutura JSON de exemplo do modelo.

````python
#main

from fastapi import FastAPI
# Optional
from typing import Optional
# pydantic
from pydantic import BaseModel

app = FastAPI()

           
class Livros(BaseModel):
    # Criado atributos do livro
    id_livro : int
    titulo : str
    autor : str
    lancamento : int

    class Config:
    schema_extra = {
        "example": {
            "id_livro": 1,
            "titulo": "Hábitos aótmicos",
            "autor": "James Clear",
            "lancamento": 2017,
        }
    }

@app.post('/livros')
async def add_livro(livros: Livros):
    return livros
````
[![image.png](https://i.postimg.cc/2yZDb34N/image.png)](https://postimg.cc/wRgPnqfw)

## Conclusão

Portanto, nesta postagem, você aprendeu como pode começar a usar o FastAPI para construir APIs de alto desempenho. Já temos uma estrutura mínima chamada Flask, mas o suporte assíncrono do FastAPI o torna muito atraente para sistemas de produção modernos, especialmente modelos de aprendizado de máquina que são acessados ​​por meio de APIs REST. Eu apenas arranhei a superfície dele. Você pode aprender mais sobre isso no site oficial da FastAPI.