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
  "id": "7weN1G2zW0KCMDVv75VDmQ",
  "nome": "Nekusar Deck",
  "formato": "Commander",
  "descricao": "Deck centrado em Nekusar, the Mindrazer, utilizando efeitos de 'wheel' para causar dano aos oponentes enquanto acelera sua própria vantagem de cartas.",
  "cartas": [
    {
      "id": 1,
      "nome": "Nekusar, the Mindrazer",
      "tipo": "Criatura Lendária",
      "cor": "Azul/Preto/Vermelho",
      "custoMana": "2UBR",
      "quantidade": 1
    },
    {
      "id": 3,
      "nome": "Windfall",
      "tipo": "Feitiço",
      "cor": "Azul",
      "custoMana": "2U",
      "quantidade": 1
    },
    {
      "id": 4,
      "nome": "Teferi's Puzzle Box",
      "tipo": "Artefato",
      "cor": "Incolor",
      "custoMana": "4",
      "quantidade": 1
    },
  ],
}
```

## CardDTO

```json
{
  "id": 3,
  "nome": "Windfall",
  "tipo": "Feitiço",
  "cor": "Azul",
  "custoMana": "2U",
  "descricao": "Cada jogador descarta sua mão e compra o mesmo número de cartas que o maior número de cartas descartadas desta forma."
}
```

## CommentDTO

```json
{
  "id": 7,
  "deckId": 1,
  "usuario": "gabriel_rossi",
  "comentario": "Esse deck é ótimo pra partidas rápidas!",
  "data": "2025-04-17T14:23:00Z"
}
```
---

# 🗂️ Especificação OpenAPI

[Download do arquivo openapi.json](./openapi.json)

O arquivo anexado acima contém a especificação completa da **Deck API** no padrão **OpenAPI 3.0**. Ele define todas as rotas da aplicação, incluindo métodos HTTP, parâmetros de caminho e de consulta, códigos de status esperados e descrições das funcionalidades.

✅ O arquivo foi validado no [Swagger Editor](https://editor.swagger.io/), garantindo conformidade com o padrão **OpenAPI**.
