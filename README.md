# go-api



- Uma API usando a linguagem **Go**

## Comando


```bash
go mod init endereço-do-repositório

go mod tidy # instala as dependencies
```

## Subindo uma imagem do postgres no docker

### Comandos

- Criando a imagem do postgres no docker

```bash
docker run -d --name api-todo -p 5432:5432 -e POSTGRES_PASSWORD=1234 postgres:13.5 
```

- Executando o postgres.

```bash
docker exec -it api-todo psql -U postgres
```

- Criando o banco de dados.

```postgres
postgres=# create database nome_db;
```

- Criando usuario e senha
  
```postgres
postgres=# create user nome_usuario;

postgres=# alter user user_todo with encrypted password '******';
```

- Concedendo permicao para o usuario no banco de dados

```postgres
postgres=# grant all privileges on database nome_db to nome_usuario;
```

- Conectando no banco de dados.

```postgres
postgres=# \c nome_db;
```

- Criando tabela.

```postgres
nome_db=# create table todos (id serial primary key, title varchar, description text, done bool default FALSE);
```

- Concedendo permissoes de acesso para o usuario nas tabelas

```postgres
nome_db=# grant all privileges on all tables in schema public to user_todo;
nome_db=# grant all privileges on all sequences in schema public to user_todo;
```