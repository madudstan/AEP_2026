# SISTEMA DE GESTÃO E REDISTRIBUIÇÃO DE ALIMENTOS EXCEDENTES

Heloísa Sayuri Silva Saito (24062631-2), Maria Eduarda de Castro Lachimia (24055202-2), Matheus Costa E Silva (2400729-2)

## INTRODUÇÃO

O desperdício de alimentos ainda constitui um problema relevante, especialmente em estabelecimentos que possuem produtos excedentes ou próximos do vencimento que ainda podem ser aproveitados. Ao mesmo tempo, existem instituições como ONGs, associações e bancos de alimentos que podem receber esses produtos e destiná-los a pessoas que necessitam de auxílio. A dificuldade de organizar e conectar esses dois lados pode fazer com que alimentos ainda aproveitáveis sejam descartados.

Nesse contexto, alinhado ao Objetivo de Desenvolvimento Sustentável da ONU **ODS 12 — Consumo e Produção Responsáveis**, desenvolvemos o **Sistema de Gestão e Redistribuição de Alimentos Excedentes**, uma solução digital voltada ao gerenciamento de alimentos excedentes, permitindo seu registro e acompanhamento de forma organizada e servindo como base para uma futura conexão entre estabelecimentos doadores e instituições receptoras.

## OBJETIVO

Este trabalho tem como objetivo apresentar uma solução tecnológica voltada à redução do desperdício de alimentos, por meio de um sistema que permite aos estabelecimentos registrar e gerenciar alimentos excedentes que ainda podem ser aproveitados.

A proposta busca organizar informações como nome, quantidade, unidade, data de validade, origem e status, criando uma base para futuras funcionalidades de redistribuição. Nesta primeira entrega, o sistema representa apenas o núcleo inicial da plataforma, sem implementar usuários, instituições, solicitações ou redistribuições.

## MÉTODO

O desenvolvimento baseou-se em conceitos de Engenharia de Software, incluindo Programação Orientada a Objetos, separação de responsabilidades, persistência de dados, versionamento e testes automatizados.

A arquitetura segue o padrão do projeto de referência da disciplina, organizada em camadas de **Controller, DTO, Service, Repository, Model e Mapper**, com tratamento de exceções e boas práticas de organização do código.

Para a primeira versão da Prova de Conceito (PoC), foi utilizada uma única coleção NoSQL, contendo objetos homogêneos e de estrutura simples, conforme os requisitos da AEP. A aplicação disponibiliza operações básicas de CRUD para o gerenciamento dos alimentos excedentes.

## DESENVOLVIMENTO E RESULTADOS

O sistema foi desenvolvido em **Java 21**, utilizando **Spring Boot** e **Spring Data MongoDB**. A entidade principal representa um alimento excedente, contendo nome, quantidade, unidade, data de validade, origem e status.

A aplicação permite cadastrar, consultar, atualizar e excluir alimentos. Foram aplicadas validações básicas para garantir a consistência dos dados, como obrigatoriedade dos campos, quantidade maior que zero e validade não anterior à data atual.

O banco utilizado é o **MongoDB**, com uma única coleção chamada `alimentos`. A solução possui testes unitários de Service e Controller e testes de integração da API utilizando Testcontainers com MongoDB. O **JaCoCo** é utilizado para medir e bloquear o build quando a cobertura de linhas fica abaixo de 70%.

## CONSIDERAÇÕES FINAIS

O Sistema de Gestão e Redistribuição de Alimentos Excedentes demonstra como a tecnologia pode contribuir para o melhor aproveitamento de alimentos e para a redução de desperdícios, estando relacionado à **ODS 12 — Consumo e Produção Responsáveis**.

A primeira versão apresenta uma base funcional para o gerenciamento de alimentos excedentes e aplica conceitos de Engenharia de Software, Programação Orientada a Objetos, banco de dados NoSQL, testes automatizados e organização arquitetural.

Como evolução futura, o projeto poderá incluir instituições receptoras, solicitações, redistribuições e as demais etapas do fluxo de aproveitamento dos alimentos.

## ODS

### ODS 12 — Consumo e Produção Responsáveis

O projeto está relacionado à ODS 12 porque busca contribuir para o melhor aproveitamento de alimentos excedentes, reduzindo desperdícios e criando uma base tecnológica para futura redistribuição dos alimentos que ainda podem ser aproveitados.

## TECNOLOGIAS UTILIZADAS

- Java 21;
- Spring Boot 3.5.16;
- Spring Web;
- Spring Data MongoDB;
- Jakarta Validation;
- Springdoc OpenAPI / Swagger UI;
- JUnit 5;
- Mockito;
- MockMvc;
- Testcontainers com MongoDB;
- JaCoCo;
- Maven Wrapper;
- Git e GitHub;
- MongoDB 7.0;
- Docker e Docker Compose.

## ARQUITETURA

O fluxo principal da aplicação é:

```text
JSON -> Controller -> Request DTO -> Service -> Repository -> MongoDB
```

O fluxo de resposta é:

```text
MongoDB -> Model -> Service -> Mapper -> Response DTO -> Controller -> JSON
```

- `Controller`: recebe e responde às requisições HTTP;
- `DTO`: define os contratos de entrada e saída;
- `Service`: concentra os casos de uso;
- `Repository`: realiza o acesso ao MongoDB;
- `Model`: representa o documento persistido;
- `Mapper`: converte DTOs e modelos;
- `Exception`: padroniza erros da API.

## BANCO DE DADOS

A primeira entrega utiliza **uma única coleção NoSQL**:

```text
alimentos
```

Os documentos possuem estrutura simples e homogênea. Exemplo:

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

Não existem múltiplas coleções, relacionamentos ou documentos aninhados nesta entrega.

## ENDPOINTS

| Método | Endpoint | Descrição |
|---|---|---|
| `POST` | `/api/alimentos` | Cadastra um alimento excedente |
| `GET` | `/api/alimentos` | Lista os alimentos cadastrados |
| `GET` | `/api/alimentos/{id}` | Consulta um alimento pelo ID |
| `PUT` | `/api/alimentos/{id}` | Atualiza um alimento |
| `DELETE` | `/api/alimentos/{id}` | Exclui um alimento |

### Validações

- `nome` obrigatório;
- `quantidade` obrigatória e maior que zero;
- `unidade` obrigatória;
- `dataValidade` obrigatória e em formato de data válido;
- `origem` obrigatória;
- `status` obrigatório e limitado aos valores definidos pela aplicação.

## PRÉ-REQUISITOS

- JDK 21;
- Docker;
- Docker Compose v2;
- Git.

O projeto inclui Maven Wrapper, portanto não é necessário instalar Maven separadamente.

Verifique:

```bash
java -version
docker --version
docker compose version
./mvnw -version
```

## EXECUÇÃO

### 1. Clonar o projeto

```bash
git clone URL_DO_REPOSITORIO
cd alimentos-excedentes-aep
```

### 2. Iniciar o MongoDB

```bash
docker compose up -d
```

Verifique os serviços:

```bash
docker compose ps
```

O MongoDB fica disponível localmente em `localhost:27018`.

Para encerrar a infraestrutura sem apagar os dados:

```bash
docker compose down
```

### 3. Executar a aplicação

No Windows:

```powershell
mvnw.cmd spring-boot:run
```

No Linux/macOS:

```bash
./mvnw spring-boot:run
```

A API ficará disponível em:

```text
http://localhost:8080
```

A documentação interativa da API fica em:

```text
http://localhost:8080/docs
```

### 4. Executar os testes

```bash
./mvnw test
```

No Windows:

```powershell
mvnw.cmd test
```

### 5. Gerar e verificar a cobertura

```bash
./mvnw clean verify
```

No Windows:

```powershell
mvnw.cmd clean verify
```

O JaCoCo gera o relatório de cobertura e o build verifica automaticamente a cobertura mínima de **70%**.

