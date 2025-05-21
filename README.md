# Trabalho 1 - Devops/ Prática com Docker

Sistema para oferta de vagas de estágios/empregos (A)<br /><br />

Esta é uma aplicação web Java Spring Boot para gerenciamento de vagas de estágio/emprego, com persistência de dados em banco MySQL e envio de e-mails via SMTP. A aplicação foi **dockerizada** e é executada com múltiplos contêineres, conforme prática solicitada para o exercício.

## 🧾 Descrição

O sistema permite que **empresas cadastrem vagas** e **profissionais se candidatem**, com autenticação, listagens e envio de status por e-mail. A arquitetura utiliza:

- Backend em **Java Spring Boot**
- Banco de dados **MySQL**
- Interface de administração com **Adminer**
- Sistema de envio de **e-mails via SMTP (Gmail)**

## 📦 Estrutura de Contêineres

Este projeto usa 3 contêineres, conforme exigência para trabalho individual:

| Serviço   | Descrição                                       | Porta       |
|-----------|-------------------------------------------------|-------------|
| `app`     | Backend Spring Boot (compilado com Maven)       | `8080`      |
| `db`      | Banco de dados MySQL                            | `3306`      |
| `adminer` | Interface para gerenciar banco (Adminer)        | `8081`      |

Todos os serviços se comunicam por **nome de contêiner**, conforme exigência do trabalho (não utilizam `localhost` entre si).

## ⚙️ Tecnologias Utilizadas

- **Java 17**
- **Spring Boot**
- **Spring Data JPA + Hibernate**
- **MySQL 8**
- **Maven**
- **Docker / Docker Compose**
- **Adminer**
- **SMTP Gmail**

## 📁 Estrutura dos Arquivos


├── Dockerfile # Build da aplicação em 2 etapas

├── docker-compose.yml # Orquestração dos contêineres

├── src/ # Código-fonte Java (Spring Boot)

├── pom.xml # Dependências Maven

├── application.properties # Configurações Spring Boot

└── README.md # Este documento

## 📝 Configuração Importante


Para executar o sistema corretamente, você precisa editar as variáveis de ambiente no docker-compose.yml e no application.properties:


🔐 Senha do MySQL

Substitua seu_username_aqui e sua_senha_aqui pela user e senha real que você usou ao instalar o MySQL no seu computador.


Exemplo: se você usa "root" como user, e "root1" como senha troque:

spring.datasource.username=seu_username_aqui

spring.datasource.password=sua_senha_aqui

por:

spring.datasource.username=root

spring.datasource.password=root1

📧 Senha do Gmail

Também é necessário fornecer um e-mail e uma senha de aplicativo do Gmail para que o envio de e-mails funcione corretamente.

## 📦 Explicação dos Arquivos Docker

## Dockerfile

Este arquivo contém duas etapas de construção:


- **Build Stage**: Usa uma imagem Maven + JDK 17 para compilar o projeto Java com mvn clean package.

- **Production Stage**: Copia o JAR gerado para uma imagem mais leve (OpenJDK) e executa o aplicativo com java -jar.

## docker-compose.yml

Este arquivo orquestra três contêineres:


- Serviço	Descrição	Porta
  
- app	Backend Spring Boot (Java)	8080
  
- db	Banco de dados MySQL	3306

- adminer	Interface web para gerenciar o banco	8081


Todos os serviços estão conectados na mesma rede (devops-net), permitindo comunicação por nome do serviço (por exemplo, db, e não localhost).

A aplicação só inicia após o banco estar saudável (depends_on + healthcheck).

## 🚀 Como Executar o Projeto com Docker

1. **Clone o repositório**

- git clone (https://github.com/natycristina/Trabalho1-devops.git)

3. **Execute os contêineres**

Execute a aplicação com Docker Compose

- docker-compose up --build

3. **Aesse a aplicação**
   
- Aplicação Spring Boot: http://localhost:8080

4. **Parar os contêineres**
   
- docker-compose down
