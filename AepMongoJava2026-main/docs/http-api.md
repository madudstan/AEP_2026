# API HTTP

Base URL local: `http://localhost:8080`

| Método | Endpoint | Resultado |
|---|---|---|
| POST | `/api/alimentos` | 201 Created |
| GET | `/api/alimentos` | 200 OK |
| GET | `/api/alimentos/{id}` | 200 OK ou 404 Not Found |
| PUT | `/api/alimentos/{id}` | 200 OK ou 404 Not Found |
| DELETE | `/api/alimentos/{id}` | 204 No Content ou 404 Not Found |

A API utiliza validação de entrada e retorna `400 Bad Request` quando os dados enviados são inválidos.
