# 🎮 GraphQL Crash Course API

A lightweight GraphQL API built with Apollo Server to demonstrate querying and mutating a dataset of video games, authors, and reviews.

**YouTube Course Link**: https://www.youtube.com/watch?v=5199E50O7SI&pp=ygUHZ3JhcGhxbA%3D%3D

## 📦 Project Structure

```
├── index.js          # Main server entry point
├── schema.js         # GraphQL schema definitions
├── _db.js            # In-memory mock database
├── package.json      # Project metadata and dependencies
├── .gitignore        # Ignored files and folders
```

## 🚀 Features

- Apollo Server v4 with standalone support
- Full GraphQL schema with:
  - Queries for Games, Authors, Reviews
  - Nested resolvers for relationships
  - Mutations to create, update, delete Games
- In-memory data mock (no database required)
- Modular, clean resolver structure

## 🧰 Tech Stack

- **Node.js** (ES Modules)
- **Apollo Server** (`@apollo/server`)
- **GraphQL** (`graphql`)
- **Nodemon** for live-reloading during development

## 🛠️ Installation

```bash
# Clone the repository
git clone <your-repo-url>
cd graphql-crash-course

# Install dependencies
npm install
```

## 🏁 Getting Started

Run the GraphQL server:

```bash
node index.js
```

The server starts at:

```
http://localhost:4000/
```

You can use [Apollo Sandbox](https://studio.apollographql.com/sandbox/explorer) or Postman to interact with the GraphQL API.

## 📌 Sample Queries

```graphql
query {
  games {
    id
    title
    platform
    reviews {
      content
      rating
    }
  }
}
```

```graphql
mutation {
  addGame(game: { title: "Hades", platform: ["PC", "Switch"] }) {
    id
    title
    platform
  }
}
```

## 🧪 Mutations Supported

- `addGame(game: AddGameInput!): Game`
- `deleteGame(id: ID!): [Game]`
- `updateGame(id: ID!, edits: EditGameInput!): Game`

## 📁 Data Model Overview

```graphql
type Game {
  id: ID!
  title: String!
  platform: [String!]
  reviews: [Review!]!
}

type Author {
  id: ID!
  name: String!
  verified: Boolean!
  reviews: [Review!]
}

type Review {
  id: ID!
  rating: Int!
  content: String!
  game: Game!
  author: Author!
}
```

## 📝 Notes

- This is a self-contained demo with an in-memory DB. Changes will not persist after a restart.
- Ideal for GraphQL learning, prototyping or hackathon backends.

## 📃 License

ISC — Feel free to use, copy, and improve this project.

---

Made with ❤️ for GraphQL learners.
