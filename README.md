# 🃏 MTG Deck Builder API - documentação

## 📃 Introdução

Essa **API RESTful** permite a criação e o gerenciamento de decks de **Magic: The Gathering (MTG)**, inspirada em plataformas como [Moxfield](https://moxfield.com/). Com ela, os usuários podem criar, editar, excluir e compartilhar decks, além de adicionar/remover cartas e visualizar mais detalhes.

---

# 🧮 Rotas da API

| Método HTTP | Rota                            | Descrição                                 | Status Codes         |
|--------|--------------------------------------|------------------------------------------------|----------------------|
| GET    | /decks                               | Listar todos os decks públicos                 | 200, 500             |
| GET    | /decks{id}                           | Criar novo deck                                | 201, 400, 500        |
| GET    | /cards                               | Listar todas as cartas disponíveis             | 200, 500             |
| GET    | /cards/{id}                          | Buscar carta por ID                            | 200, 404, 500        |
| GET    | /decks/{id}/stats                    | Estatísticas do deck                           | 200, 404, 500        |
| GET    | /decks/user/{userId}                 | Listar decks de um usuário específico          | 200, 404, 500        |
| GET    | /decks/{id}/comments                 | Listar comentários do deck                     | 200, 404, 500        |
| GET    | /decks/search?query=...              | Buscar decks por nome ou formato               | 200, 400, 500        |
| POST   | /decks                               | Criar novo deck                                | 201, 400, 500        |
| POST   | /decks/{id}/cards                    | Adicionar cartas ao deck                       | 200, 400, 404, 500   |
| POST   | /cards                               | Cadastrar nova carta                           | 201, 400, 500        |
| POST   | /decks/{id}/like                     | Curtir um deck                                 | 200, 404, 500        |
| POST   | /decks/{id}/comments                 | Adicionar comentário ao deck                   | 201, 400, 404, 500   |
| PUT    | /decks/{id}                          | Atualizar deck existente                       | 200, 400, 404, 500   |
| PUT    | /cards/{id}                          | Atualizar carta existente                      | 200, 400, 404, 500   |
| DELETE | /decks/{id}                          | Excluir deck existente                         | 204, 404, 500        |
| DELETE | /decks/{id}/cards/{cardId}           | Remover carta do deck                          | 204, 404, 500        |
| DELETE | /cards/{id}                          | Excluir carta                                  | 204, 404, 500        |
| DELETE | /decks/{id}/like                     | Remover curtida do deck                        | 204, 404, 500        |
| DELETE | /decks/{id}/comments/{commentId}     | Remover comentário                             | 204, 404, 500        |

---

# 🎲 DTOs e Modelos de Dados

## DeckDTO

```json
{
  "DeckDTO": {
    "id": "integer",
    "nome": "string",
    "formato": "string",
    "descricao": "string",
    "cartas": [
      {
        "id": "integer",
        "nome": "string",
        "tipo": "string",
        "cor": "string",
        "custoMana": "string",
        "quantidade": "integer"
      }
    ],
    "dataCriacao": "string"
  }
}
```

## CardDTO

```json
{
  "CardDTO": {
    "id": "integer",
    "nome": "string",
    "tipo": "string",
    "subtipo": "string",
    "supertipo": "string",
    "cor": "string",
    "custoMana": "string",
    "habilidades": [
      "string"
    ],
    "textoDoSabor": "string",
    "poder": "integer",
    "resistencia": "integer"
  }
}
```

---

# 🗂️ Especificação OpenAPI

[Download do arquivo openapi.json](./openapi.json)

O arquivo anexado acima contém a especificação completa da **Deck API** no padrão **OpenAPI 3.0**. Ele define todas as rotas da aplicação, incluindo métodos HTTP, parâmetros de caminho e de consulta, códigos de status esperados e descrições das funcionalidades.

✅ O arquivo foi validado no [Swagger Editor](https://editor.swagger.io/), garantindo conformidade com o padrão **OpenAPI**.
