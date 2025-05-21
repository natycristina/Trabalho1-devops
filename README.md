# Trabalho 1 - Devops/ Prática com Docker

Sistema para oferta de vagas de estágios/empregos (A)<br /><br />

Este projeto é uma aplicação web Java Spring Boot para gerenciamento de vagas de estágio/emprego, com persistência de dados em banco MySQL e envio de e-mails via SMTP. A aplicação foi **dockerizada** e é executada com múltiplos contêineres, conforme prática solicitada para o exercício.

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

.
├── Dockerfile # Build da aplicação em 2 etapas
├── docker-compose.yml # Orquestração dos contêineres
├── src/ # Código-fonte Java (Spring Boot)
├── pom.xml # Dependências Maven
├── application.properties # Configurações Spring Boot
└── README.md # Este documento

## 🚀 Como Executar o Projeto com Docker

1. **Clone o repositório**
2. 
= git clone (https://github.com/natycristina/Trabalho1-devops.git)

cd (a basta onde foi clonado o repositorio)

no meu caso:
= cd C:\Users\Nataly\Documents\Devops\Trabalho1\Trabalho1-devops>

3. **Comando para Compilar**
4. 
Execute a aplicação com Docker Compose

- docker-compose up --build

4. **Aesse a aplicação**

Acesse:

- Aplicação Spring Boot: http://localhost:8080




Arquivos de Configuração
Dockerfile
O arquivo Dockerfile para a aplicação Spring Boot utiliza uma abordagem de múltiplos estágios:

Primeiro estágio: compila o código-fonte Java com Maven
Segundo estágio: cria uma imagem mais leve apenas com o arquivo JAR executável 

Para parar os contêineres:
docker-compose down
