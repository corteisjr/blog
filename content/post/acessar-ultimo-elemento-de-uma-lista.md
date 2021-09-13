---
title: "Acessar Ultimo Elemento De Uma Lista"
date: 2021-09-14T00:11:54+02:00
draft: true
---

# Pegar o ultimo elemento de uma lista em Python

Listas são usadas para armazenar diferentes  items em uma variável, Lista é um dos 4 tipos de dados usados
para armazenar coleções de dados, os outros 3 são: 

- Tupla;
- Set;
- Dicionário.

O nosso objectivo hoje é aprender as diferentes formas/métodos que podemos usar para pegar o ultimo elemento em uma lista.
Para tal, nós usaremos meios como, **indexação**, **pop()**, **fatiamento** e **iteração reversa**.

## Pegar o ultímo elemento usando o método de Indexação
---
Em python, nós podemos usar índices positivos e negativos. os índices positivos são aqueles que começam com zero(0) que correspondem ao primeiro elemente dentro de uma lista e os negativos são os que começam com (-1) que correspondem ao ultimo elemento.

certo, um jeito simples de pegar o ultímo elemento de uma lista seria:

````python

    a = [1,2,3,4,5,6,7,8]
    print(a[-1])
````

saída

``` {r, results='hide'}
    8
```

Facíl ném? Espere aí e se nós tivermos uma lista com um número de itens que não conheçamos... hummm😕.
É simples, nós podemos primeiro achar o tamanho da lista usando a função **len()**, depois nós podemos acessar o último
elemento da lista subtraindo o "tamanhaLista-1", veja a baixo.

````python

    a = [1,2, 5, 6, 7, 8, 9,"Casa nerd"] #Vamos supor que está lista têm um número de itens que não conheçamos.
    print("Lista dada: ", a)
    tamanhoLista = len(a)
    ultElemento = a[tamanhoLista-1]
    print("O nosso último elemento é: ", ultElemento)

````

saída

``` {r, results='hide'}
    
    O nosso último elemento é: Casa nerd
```
 
## Usando o método Pop()
---