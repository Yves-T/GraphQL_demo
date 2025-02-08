# GraphQL demo

## Setup

- Run `pnpm install`
- Run `pnpm run dev`

## Example queries

Go to [localhost](http://localhost:4000) to open the GraphQl sandbox

### Get all games

```graphql
query GameQuery {
  games {
    title
  }
}
```

### Query with variables

Receive a game with specific id

```graphql
query GameQuery($id: ID!) {
  game(id: $id) {
    title
    platform
    id
  }
}
```

Variables:

```json
{
  "id": "1"
}
```

### Get related data

Get a review with related game

```graphql
query ReviewQuery($id: ID!) {
  review(id: $id) {
    rating
    game {
      title
      platform
    }
  }
}
```

Variables:

```json
{
  "id": "2"
}
```

## Example Mutations

### Add Mutation

Add a game

```graphql
mutation AddMutation($game: AddGameInput!) {
  addGame(game: $game) {
    id
    title
    platform
  }
}
```

Variables:

```json
{
  "game": {
    "title": "a new game",
    "platform": ["switch", "ps5"]
  }
}
```

### Delete Mutation

Delete a game with id 2

```graphql
mutation DeleteMutation($id: ID!) {
  deleteGame(id: $id) {
    id
    title
    platform
  }
}
```

Variables:

```json
{
  "id": "2"
}
```

### Edit Mutation

Edit a game:

editMutation:

```graphql
mutation editMutation($edits: EditGameInput!, $id: ID!) {
  updateGame(edits: $edits, id: $id) {
    title
    platform
  }
}
```

Variables

```json
{
  "edits": {
    "title": "dark souls"
  },
  "id": "2"
}
```
