---
title: "Acessar Ultimo Elemento De Uma Lista"
date: 2021-09-14T00:11:54+02:00
draft: false
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
    Lista dada: [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    O último elemento da lista é: Casa nerd
```
 
## Usando o método Pop()
---

o método pop () é usado para remover um elemento na lista (por padrão, o último elemento), e retorna o valor desse elemento, por outra, ele pega o índice do elemento como parâmetro de entrada opcional e retorna o elemento no índice 
especificado após excluí-lo da lista.
Como usar este método:

````python

      a = [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
      print("Lista dada: ", a)
      print("O último elemento da lista é: ", a.pop())
````

saída

``` {r, results='hide'}
    Lista dada: [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    O último elemento da lista é: Casa nerd
```

> [!Atenção]
> Ao usar o método pop(), ele apaga definitavamente o item da lista.
> 
> Use este método somente quando quiseres eliminar o último elemento da lista.

## Pegar o último elemento da lista usando fatiamento
---

Em python, fatiamento é uma operação para criar uma sub-parte de uma string ou uma lista. Com o
fatiamento, podemos acessar diferentes partes de alguma string, tupla ou lista.
Para realizar fatiamenento em uma lista chamada, nós usamos a seguinte sintaxe **nomeDaLista[inicio, fim, intervalo]** onde "início" e "fim" são índices na qual a lista fatiada começa e termina na lista original, respectivamente.
O *intervalo* é usado para selecionar os elementos em uma sequência. Os elementos são selecionados da lista nos índices que são múltiplos de números inteiros de “intervalo” longe do índice inicial.

Para acessar o último elemento de uma lista usando fitiamenento em python, podemos fatiar uma lista de forma que contenha apenas o último elemento. Então, podemos acessar esse elemento da seguinte maneira.

````python

    a = [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    print("Lista dada: ", a)
    ultElemento = a[-1:][0]
    print("O último elemento da lista é: ", ultElemento)
````

saída

``` {r, results='hide'}
    Lista dada: [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    O último elemento da lista é: Casa nerd
```

## Acessar o último elemento de uma lista usando iterador reverso

Podemos usar o iterador reverso para acessar o último elemento de uma lista. Para criar o iterador reverso, podemos usar
o método *reversed()*. O método *reversed()* pega qualquer objeto iterável como entrada e retorna um iterador reverso do iterável.

Para acessar o último elemento de uma lista, podemos criar primeiro  um iterador reverso de uma lista usando o método
*reversed()*. Então vamos acessar o primeiro elemento do iterador reverso que poderá ser o último elemento da lista original. Veja!


````python

    a = [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    print("Lista dada: ", a)
    IterReverso = reversed(a)
    ultElemento = next(iterReverso)
    print("O último elemento da lista é: ", ultElemento)
````

saída

``` {r, results='hide'}
    Lista dada: [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    O último elemento da lista é: Casa nerd
```

## Obtenha o último elemento de uma lista usando itemgetter

Podemos criar um objeto itemgetter para acessar o último elemento de uma lista. O método itemgetter () é definido no módulo do operador em python. O método itemgetter () recebe o índice como entrada, o que cria um objeto que pode ser chamado. O objeto chamável pega um iterável como entrada e extrai o elemento no índice especificado.

Para acessar o último elemento da lista, podemos chamar o método itemgetter () com o índice de entrada como -1 e então podemos acessar o último elemento da lista como segue.


````python

    import operator

    a = [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    print("Lista dada: ", a)
    ultElemento = operator.itemgetter(-1)(a)
    print("O último elemento da lista é: ", ultElemento)
````

saída

``` {r, results='hide'}
    Lista dada: [1,2, 5, 6, 7, 8, 9,"Casa nerd"]
    O último elemento da lista é: Casa nerd
```

### Conclusão

Neste artigo, nós vimos diferentes formas de acessar o último elemento de uma lista em python, subscreva-se no newsletter para se manter informado as próximas dicas.