Funcionalidades

Gêneros:
Cadastro de gênero com:
ID (3 caracteres)
Descrição (até 35 caracteres)
Listagem, atualização e exclusão de registros

Filmes:
Cadastro de filmes com:
ID (auto-incremento)
Título (até 40 caracteres)
Ano de produção
Duração em minutos
Gênero (chave estrangeira)

Listagem, atualização e exclusão de registros


Menu Principal:
Navegação entre os módulos Filmes e Gêneros

Tecnologias Utilizadas:
Java 21 (Swing)
PostgreSQL
JDBC
NetBeans 25


Estrutura do Projeto:
cineminha/
│
├─ Filme.java        // Modelo de filme
├─ Genero.java       // Modelo de gênero
├─ FilmeDAO.java     // CRUD de filmes (DAO)
├─ GeneroDAO.java    // CRUD de gêneros (DAO)
├─ FilmeView.java    // Interface Swing de filmes
├─ GeneroView.java   // Interface Swing de gêneros
├─ Conexao.java      // Gerenciamento da conexão PostgreSQL
└─ Cineminha.java    // Classe principal (menu)



Configuração do Banco de Dados
Crie o banco de dados no PostgreSQL:

CREATE DATABASE cineminha;
Crie as tabelas:

CREATE TABLE genero (
    id_genero CHAR(3) PRIMARY KEY,
    descricao VARCHAR(35) NOT NULL
);

CREATE TABLE filme (
    id_filme SERIAL PRIMARY KEY,
    titulo VARCHAR(40) NOT NULL,
    ano_producao INTEGER NOT NULL,
    duracao_minutos INTEGER NOT NULL,
    id_genero CHAR(3) NOT NULL,
    FOREIGN KEY (id_genero) REFERENCES genero(id_genero)
);


Configure as credenciais em Conexao.java:

private static final String URL = "jdbc:postgresql://localhost:5432/cineminha";
private static final String USER = "postgres";
private static final String PASSWORD = "postgres";


⚠️ Certifique-se de adicionar o driver JDBC do PostgreSQL ao projeto.

Como Executar:
Abra o projeto no NetBeans.
Compile e execute a classe Cineminha.java.
Utilize o menu para acessar os módulos de Filmes ou Gêneros.


Observações:
Verifique se a URL do JDBC aponta para o banco correto.

Caso ocorra erro de driver não encontrado, confirme se o JAR do PostgreSQL está corretamente configurado.

IDs:

Filmes: numéricos

Gêneros: exatamente 3 caracteres
