# Arquitetura da PoC

A primeira entrega segue a organização do projeto de referência do professor, adaptada ao domínio de alimentos excedentes.

```text
JSON -> Controller -> Request DTO -> Service -> Repository -> MongoDB
```

Para respostas:

```text
MongoDB -> Model -> Service -> Mapper -> Response DTO -> Controller -> JSON
```

## Camadas

- `controller`: endpoints HTTP;
- `dto`: contratos de entrada e saída;
- `service`: casos de uso;
- `repository`: persistência MongoDB;
- `model`: documento `Alimento` e enum de status;
- `mapper`: conversão entre DTO e Model;
- `exception`: tratamento padronizado de erros;
- `configuration`: configuração do OpenAPI.

A primeira entrega possui uma única coleção MongoDB: `alimentos`.
