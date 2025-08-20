📚 FórumHub API

API desenvolvida em Spring Boot 3 para gerenciamento de tópicos em um fórum.
O projeto utiliza MySQL como banco de dados, Spring Data JPA para persistência e Flyway para migrations.

🗄️ Modelagem do Banco de Dados

A entidade principal é Tópico, com os seguintes campos obrigatórios:

id (PK)

titulo

mensagem

dataCriacao

status

autor

curso

📌 Exemplo de tabela topicos em SQL:

CREATE TABLE topicos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    mensagem TEXT NOT NULL,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(50) NOT NULL,
    autor VARCHAR(255) NOT NULL,
    curso VARCHAR(255) NOT NULL,
    UNIQUE (titulo, mensagem)
);


⚠️ O diagrama pode conter outras tabelas (ex: usuários, cursos), mas para este challenge é suficiente focar na tabela de tópicos.

⚙️ Configuração do Projeto
Dependências no pom.xml

Spring Web

Spring Data JPA

MySQL Driver

Validation

Flyway Migration

Configuração no application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/forumhub
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=none
spring.jpa.show-sql=true

spring.flyway.enabled=true

🚀 Migrations com Flyway

As migrations devem ser criadas na pasta:

src/main/resources/db/migration


Exemplo de arquivo V1__create_table_topicos.sql:

CREATE TABLE topicos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    mensagem TEXT NOT NULL,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status VARCHAR(50) NOT NULL,
    autor VARCHAR(255) NOT NULL,
    curso VARCHAR(255) NOT NULL,
    UNIQUE (titulo, mensagem)
);

📌 Endpoints da API
1. Criar Tópico

POST /topicos

Corpo da requisição (JSON):

{
  "titulo": "Erro ao criar projeto Spring",
  "mensagem": "Não consigo configurar o MySQL",
  "autor": "João Silva",
  "curso": "Spring Boot"
}

2. Listar Tópicos

GET /topicos

Retorna lista com todos os tópicos cadastrados.

3. Detalhar Tópico por ID

GET /topicos/{id}

Retorna os detalhes de um tópico específico.

4. Atualizar Tópico

PUT /topicos/{id}

Corpo da requisição (JSON):

{
  "titulo": "Erro corrigido",
  "mensagem": "Consegui resolver configurando o application.properties"
}

5. Deletar Tópico

DELETE /topicos/{id}

Remove o tópico do banco de dados.

✅ Regras de Negócio

Todos os campos são obrigatórios.

Não é permitido cadastrar tópicos duplicados (mesmo título e mensagem).

O ID deve ser validado antes de detalhar, atualizar ou excluir um tópico.

🔧 Tecnologias Utilizadas

Java 17+

Spring Boot 3

Spring Data JPA

Flyway

MySQL

Maven

▶️ Como Executar o Projeto

Clonar o repositório

git clone https://github.com/seu-repo/forumhub.git


Configurar o banco de dados MySQL.

Ajustar application.properties com suas credenciais.

Executar as migrations com Flyway.

Rodar o projeto:

mvn spring-boot:run

🛠 Sugestões Extras

Paginação e ordenação dos tópicos.

Busca por curso ou ano de criação.

Implementação de autenticação (JWT).

Integração com Swagger para documentação da API.

📖 Conteúdo de apoio:

Spring Data JPA Docs

Validation in Spring Boot

Curso Spring Boot 3 - Alura
