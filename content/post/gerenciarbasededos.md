---
title: "Gerenciar base dedos Parte 1"
date: 2021-09-09T23:02:54+02:00
draft: true
---


# Como criar e Gerenciar Banco de Dados e Tabelas

-------------

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

Usando o comando **create database nome_da_BaseDeDados**, estamos dizendo ao myqsl para criar uma base de dados com o nome **Música**.

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

