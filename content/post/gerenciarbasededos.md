---
title: "Gerenciar base dedos Parte 1"
date: 2021-09-09T23:02:54+02:00
draft: false
---
# Como criar e Gerenciar Banco de Dados e Tabelas
---
Para o gerenciamente básico de uma base de dados em Mysql é necessário saber:

- Criar uma base de dados com **CREATE DATABASE**;
- Conhecer os **tipos de dados**;
- Saber o que são chaves - chave primária, chave estrangeira e outras;
- Saber o que é **CONSTRAINT**;
- Saber **CRIAR** tabela;
- Saber **RENOMEAR** Tabelas;
- Saber como **MODIFICAR** Tabelas;
- Saber **EXCLUIR** tabelas;

## Criando uma base de dados

````sql
    
    Mysql> create database Musica;
````

Usando o comando **create database nome_da_BaseDeDados**, estamos dizendo ao myqsl para criar uma base de dados com o nome **Musica**.

## Usando a base de Dados

````sql

    Mysql> use database Musica

````

## Tipos de dados

![alt text](https://miro.medium.com/max/2400/1*MWGJF0l5g6pb6_3YZAFJwA.png)


> [!NOTE]
>Vale realçar que a tabela não fornece todos os tipos de dados, existem outros que você pode achar dando um pesquisa rápida.

### Quando usar qual?

Não existem regras específicas, tudo vai de acordo com o uso e ao que se pretende fazer. É só dar uma olhada na tabela acima e botar a mão na massa.

## O que são chaves?

Chaves na base de dados seriam **campos de um registro**, campos estes que podem ser:

- Uma chave é dita única se ela identifica, de forma inequívoca, um determinado item armazenado no repositório. Uma chave não-única, ou ambígua, identifica mais de um item dentro do repositório.

- Uma chave primária é uma chave única, utilizada como referência preferencial para identificar um item dentro de um repositório. Por exemplo, o nome de um usuário de um sistema informatizado, ou o número de registro de um carro, podem ser utilizados como chaves primárias para localizar os respectivos itens.

- Uma chave estrangeira é uma chave armazenada em um determinado repositório, que permite localizar informações contidas em outros regitros.

- Uma chave simples é associada a um único valor, ou campo, do registro. Uma chave composta corresponde à combinação de duas ou mais chaves, e pode ser necessária para eliminar a ambiguidade, formando um identificador único.

> [!IMPORTANTE]
> Informação retirada da Wikipedia

## Constraints (Restrições)

São usadas para definir regras para aceitar ou restringir valores que podem ser armazenados em coluna, o próposito de introduzir o **constraints** é para reforçar a integridade de uma base de dados.
O Constraints são usados para limitar o tipo de dado que podem ser inserido na tabela, elas podem ser classificadas em dois tipos:

- Nivel de coluna; 
- Nivel de tabela.

A constraints podem ser aplicadas apenas a uma coluna onde, como restrições de nível de tabela, são aplicadas a toda a tabela.
A CONSTRAINT é declarada no momento da criação de uma tabela.

### As constraints podem ser: 

- NOT NULL
- UNIQUE
- PRIMARY KEY
- FOREIGN KEY
- CHECK
- DEFAULT

|  **Constraints**| **Descrição**  |
|---------|---------|
|NOT NULL     |   No MySQL a restrição NOT NULL permite especificar que uma coluna não pode conter nenhum valor NULL. MySQL NOT NULL pode ser usado para CRIAR e ALTERAR uma tabela      |
|UNIQUE     |  A restrição UNIQUE no MySQL não permite inserir um valor duplicado em uma coluna. A restrição UNIQUE mantém a exclusividade de uma coluna em uma tabela. Mais de uma coluna UNIQUE pode ser usada em uma tabela.       |
|PRIMARY KEY     | Uma restrição PRIMARY KEY para uma tabela força a tabela a aceitar dados exclusivos para uma coluna específica e essa restrição cria um índice exclusivo para acessar a tabela mais rapidamente.        |
|FOREIGN KEY     |      A FOREIGN KEY no MySQL cria um link entre duas tabelas por uma coluna específica de ambas as tabelas. A coluna especificada em uma tabela deve ser uma PRIMARY KEY e referida pela coluna de outra tabela conhecida como FOREIGN KEY   |
|CHECK     |    Uma restrição CHECK controla os valores na coluna associada. A restrição CHECK determina se o valor é válido ou não de uma expressão lógica.     |
|DEFAULT     |    Em uma tabela MySQL, cada coluna deve conter um valor (incluindo NULL). Ao inserir dados em uma tabela, se nenhum valor for fornecido a uma coluna, a coluna obtém o valor definido como DEFAULT.     |


🥱😀 Vamos dar uma pausa, continuaremos na segunda parte, **subscreva-se** para ter o acesso em primeira mão.

