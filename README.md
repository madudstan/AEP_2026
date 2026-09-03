 # SISTEMA DE GESTÃO E REDISTRIBUIÇÃO DE ALIMENTOS EXCEDENTES

Heloísa Sayuri Silva Saito (24062631-2), Maria Eduarda de Castro Lachimia (24055202-2), Matheus Costa E Silva (2400729-2)

## INTRODUÇÃO

O desperdício de alimentos representa um problema social e ambiental relevante, especialmente quando produtos excedentes ou próximos do vencimento, que ainda podem ser aproveitados, são descartados. Estabelecimentos do setor alimentício nem sempre possuem mecanismos para registrar e disponibilizar esses alimentos a instituições como ONGs, associações e bancos de alimentos, que podem receber esses produtos e destiná-los a pessoas que necessitam de auxílio. Nesse contexto, alinhada ao Objetivo de Desenvolvimento Sustentável 12 da ONU **(ODS 12 — Consumo e Produção Responsáveis)**, propõe-se uma plataforma digital para gerenciar a redistribuição de alimentos excedentes, contribuindo para a redução do desperdício e para o melhor aproveitamento dos recursos disponíveis.

## OBJETIVO

Este trabalho tem como objetivo apresentar uma Prova de Conceito de um sistema voltado ao cadastro e ao gerenciamento de alimentos excedentes. A solução busca permitir que estabelecimentos registrem informações como nome do alimento, quantidade, unidade de medida, data de validade, origem e status de disponibilidade. Nesta primeira entrega, a proposta concentra-se na organização dessas informações e na disponibilização de operações básicas de cadastro, consulta, atualização e exclusão. Dessa forma, o sistema representa o núcleo inicial de uma plataforma que poderá futuramente conectar estabelecimentos doadores a instituições receptoras e acompanhar o processo de redistribuição.

## MÉTODO

O desenvolvimento da solução baseia-se em conceitos de Engenharia de Software, Programação Orientada a Objetos, organização em camadas, testes automatizados e utilização de banco de dados NoSQL. A arquitetura será estruturada de modo a separar as responsabilidades entre as camadas **Model, DTO, Controller, Service, Repository e Mapper.** Para a persistência dos dados, será utilizado o **MongoDB**, com uma única coleção destinada ao armazenamento dos alimentos. Também serão aplicadas validações básicas, como a obrigatoriedade do nome, a exigência de quantidade maior que zero, o preenchimento da unidade e da origem, a utilização de uma data de validade válida e a verificação de um status válido. Os testes automatizados deverão verificar os principais comportamentos da aplicação e apresentar cobertura mínima de 70% sobre o código desenvolvido.

## DESENVOLVIMENTO

A PoC será implementada em **Java**, utilizando **Spring Boot** e **Spring Data MongoDB**, com uma estrutura orientada a objetos para representar os alimentos excedentes e suas operações. A aplicação deverá disponibilizar endpoints para **cadastrar, listar, consultar, atualizar e excluir** alimentos por meio de uma API. As respostas e os erros serão organizados com o uso de DTOs e exceções específicas, proporcionando maior clareza e padronização na comunicação entre o usuário e a aplicação. Dessa forma, a primeira versão permitirá demonstrar o registro e o gerenciamento de alimentos excedentes armazenados em uma única coleção no MongoDB.

## CONSIDERAÇÕES FINAIS

O **Sistema de Gestão e Redistribuição de Alimentos Excedentes** busca demonstrar como a tecnologia pode contribuir para o enfrentamento do desperdício e para o uso mais responsável dos alimentos disponíveis. Em sua primeira versão, a PoC organizará o registro dos excedentes e estabelecerá uma base funcional para futuras etapas de conexão entre doadores e instituições receptoras. Como próximos passos, prevê-se a evolução da plataforma por meio da inclusão de múltiplas coleções, do cadastro de usuários e instituições, do desenvolvimento de solicitações de alimentos e do acompanhamento do processo de redistribuição.

---

# ODS

## ODS 12 — Consumo e Produção Responsáveis

O projeto está relacionado à **ODS 12**, pois busca contribuir para o consumo e a produção responsáveis por meio do melhor aproveitamento de alimentos excedentes. A solução procura organizar o registro de alimentos que ainda podem ser aproveitados, criando uma base tecnológica para reduzir desperdícios e possibilitar sua futura redistribuição para instituições que possam utilizá-los.

---

# TECNOLOGIAS UTILIZADAS

## Linguagem de programação

* **Java 21**

## Framework e bibliotecas

* **Spring Boot**
* **Spring Data MongoDB**
* **Spring Validation**
* **Springdoc OpenAPI**
* **JUnit**
* **Mockito**
* **MockMvc**
* **Testcontainers**
* **JaCoCo**

## Banco de dados

* **MongoDB**

A primeira entrega utiliza uma única coleção NoSQL, contendo objetos homogêneos e de estrutura simples.

## Gerenciamento do projeto

* **Apache Maven**
* **Git**
* **GitHub**

## Aplicativos necessários

Para executar o projeto localmente, é necessário possuir:

* **JDK 21**
* **MongoDB**
* **Apache Maven** ou utilizar o Maven Wrapper disponibilizado no projeto
* **Git**, para clonar o repositório
* Uma IDE ou editor de código compatível com Java, como **IntelliJ IDEA**, **Eclipse** ou **Visual Studio Code**

---

# ESTRUTURA DA APLICAÇÃO

A aplicação segue uma arquitetura organizada em camadas:

```text
Controller
    ↓
DTO
    ↓
Service
    ↓
Repository
    ↓
MongoDB
```

O projeto também utiliza classes de **Model**, **Mapper** e **Exception** para manter as responsabilidades separadas e facilitar a manutenção e evolução da aplicação.

---

# BANCO DE DADOS

Na primeira entrega é utilizada uma única coleção:

```text
alimentos
```

Os documentos possuem uma estrutura simples e homogênea, representando os alimentos excedentes cadastrados.

Exemplo:

```json
{
  "id": "123",
  "nome": "Arroz",
  "quantidade": 20,
  "unidade": "kg",
  "dataValidade": "2026-09-10",
  "origem": "Supermercado Esperança",
  "status": "DISPONIVEL"
}
```

---

# CRUD

A primeira versão disponibiliza as operações básicas de gerenciamento dos alimentos excedentes:

```text
POST   /api/alimentos
GET    /api/alimentos
GET    /api/alimentos/{id}
PUT    /api/alimentos/{id}
DELETE /api/alimentos/{id}
```

### POST
Cadastra um novo alimento excedente.

### GET
Lista os alimentos cadastrados.

### GET /{id}
Consulta um alimento específico pelo seu identificador.

### PUT
Atualiza os dados de um alimento cadastrado.

### DELETE
Exclui um alimento cadastrado.

---

# INSTRUÇÕES BÁSICAS DE EXECUÇÃO

## 1. Pré-requisitos

Instale e configure:

* JDK 21;
* MongoDB;
* Git.

## 2. Clonar o projeto

Clone o repositório do GitHub:

```bash
git clone https://github.com/madudstan/AEP_2026
```

Entre na pasta do projeto:

```bash
cd AEP_2026
```

## 3. Iniciar o MongoDB

Certifique-se de que o serviço do MongoDB esteja em execução antes de iniciar a aplicação.
A aplicação deverá utilizar a configuração de conexão definida no projeto.

## 4. Executar a aplicação

No Windows, utilizando o Maven Wrapper:

```bash
mvnw.cmd spring-boot:run
```

Ou, caso o Maven esteja instalado:

```bash
mvn spring-boot:run
```

## 5. Executar os testes

Para executar todos os testes automatizados:

```bash
mvnw.cmd test
```

Ou:

```bash
mvn test
```

## 6. Verificar a cobertura

Para executar os testes e gerar o relatório de cobertura utilizando o JaCoCo:

```bash
mvnw.cmd clean verify
```

O relatório de cobertura será gerado pelo JaCoCo após a execução do processo de build.
A cobertura mínima exigida pela AEP é de **70%**.

