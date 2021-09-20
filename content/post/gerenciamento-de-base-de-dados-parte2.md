---
title: "Gerenciamento De Base De Dados Parte2"
date: 2021-09-16T00:33:03+02:00
draft: false
---


# Criando e usando uma base de dados

Para criarmos uma base de dados é necessário que acessemos o nosso command line client do Mysql, o commandline pedirá para você adicionar a senha caso tenho colocado durante a instalação.

**Comandos básicos**

- Show databases; - permite a visualição de todas as base de dados criadas.
- create database nome_da_base_de_dados; - permite a criação da base de dados.
- use nome_da_base_de_dados; permite usar a base de dados desejada e começar a fazer as alterações.

````Mysql

    create database editora;
    use editora;
````


### O comando create database 

---

A instrução *Create database*, como o nome sugere! serve para criarmos uma base de dados, a sintaxe para criar uma base de dados é:


### Criando tabela

Para começar a criação de uma tabela precisamos saber os seguintes detalhes -

- Nome da tabela

- Nome dos campos

- Definição de cada campo

A sintaxe para criar uma tabela é - 

````Mysql
    CREATE TABLE NOME_DA_TABELA (NOME_DA_COLUNA TIPO_DE_DADO);
````

Agora vamos criar uma base de dados para armazer informações de um livro, veja abaixo.

````mysql
    create table livro(
        id_livro int not null auto_increment,
        titulo_livro varchar(100) not null,
        autor_livro varchar(50) not null,
        descricao_livro varchar(400),
        lancamento date,
        primary key (id_livro)

    );

````

Certo, algumas coisas acima precisam de explicação -

- Campos com o atributo **NOT NULL** está sendo usado porque nós não queremos que estes campos sejam nulos, isto é, se o usuário tentar criar um registro com valor Null, o MySQL gerará um erro. Ou seja, este campos devem ser sempre preenchidos ao se fazer um cadastro.

- Campos com o atributo **AUTO_INCREMENT** diz ao MySQL para seguir em frente e adicionar o próximo número disponível para o campo id.

- A palavra chave **PRIMARY KEY** é usado para definir a coluna como uma chave primária, você pode usar múltiplas colunas separadas por uma vírgula para definar uma chave primária.

> [!NOTE]
> MySQL não termina o comando antes de voce digitar ponto e vírgula (;) no final de um comando SQL.

````Mysql

    mysql> show tables;
    +-------------------+
    | Tables_in_editora |
    +-------------------+
    | livro             |
    +-------------------+
    1 row in set (0.00 sec)

````

O camando show tables, nos mostra as tabelas que já foram criadas...

### Renomear tabela

Existiram casos em que a gente vai escrever mal o nome da nossa tabela, então precisaremos renomear a tabela.

A sintaxe para renomear uma tabela é -

````Mysql

    mysql > alter table nome_da_tabela rename to novo_nome;

````

Vamos mudar o nome da nossa tabela para livros...

````Mysql

      mysql> alter table livro rename to livros;
      Query OK, 0 rows affected (0.86 sec)

      mysql> show tables;
      +-------------------+
      | Tables_in_editora |
      +-------------------+
      | livros            |
      +-------------------+
      1 row in set (0.00 sec)

````

## Modificar tabelas;

O comando *Alter table* é usado para adicionar, deletar, ou modificar colunas em uma tabela existente. Não só como também é usado para adicionar e apagar varios *Constraints* em uma tabela existente.

**ALTER TABLE - Adicionando coluna**

Para adicionar uma coluna em uma tabela, nós usamos a seguinte sintaxe - 

````Mysql

    Alter table nome_da_tabela add nome_da_coluna tipo_de_dado;

````
Vamos adicionar uma coluna a nossa tabela livros -

````Mysql

  mysql> alter table livros add column clasificacao int(2);
  Query OK, 0 rows affected, 1 warning (0.81 sec)
  Records: 0  Duplicates: 0  Warnings: 1

  
mysql> desc livros;
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| id_livro        | int          | NO   | PRI | NULL    | auto_increment |
| titulo_livro    | varchar(100) | NO   |     | NULL    |                |
| autor_livro     | varchar(50)  | NO   |     | NULL    |                |
| descricao_livro | varchar(400) | YES  |     | NULL    |                |
| lancamento      | date         | YES  |     | NULL    |                |
| clasificacao    | int          | YES  |     | NULL    |                |
+-----------------+--------------+------+-----+---------+----------------+
6 rows in set (0.00 sec)
````
o comando *desc livros* serve para descrever a tabela

**ALTER TABLE - apagar coluna**

Para deletar uma coluna em uma table, usa-se o seguinte sintax

````Mysql

    alter table nome_tabela drop column nome_coluna;
````

vamos usar esse comando na nossa base de dados? vamos apagar a coluna lançamento.

````Mysql


mysql> alter table livros drop column lancamento;
Query OK, 0 rows affected (2.50 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc livros;
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| id_livro        | int          | NO   | PRI | NULL    | auto_increment |
| titulo_livro    | varchar(100) | NO   |     | NULL    |                |
| autor_livro     | varchar(50)  | NO   |     | NULL    |                |
| descricao_livro | varchar(400) | YES  |     | NULL    |                |
| clasificacao    | int          | YES  |     | NULL    |                |
+-----------------+--------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)



````
> [!ATenção]
> Algumas sistemas de base de dados não aceitam deletar a coluna devido a integridade e o relacionamento.

Por hoje podemos parar por aqui, depois a gente continua...
