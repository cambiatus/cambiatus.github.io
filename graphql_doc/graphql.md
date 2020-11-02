# GraphQL

## **Table of Contents**

- [Intro](#intro) 
- [Development](#development)
- [Additional Resources](#additional-resources)

## **Intro**

**What is GraphQL?**

GraphQL is a query language for our API, and a server-side runtime for executing queries by using a type system you define for your data. GraphQL isn't tied to any specific database or storage engine and is instead backed by your existing code and data.

For more information go to their main documentation page listed in the additional resources section.

**Queries & Mutations?**

Queries and Mutations are how GraphQL gives superpowers to its clients (ex: Frontend) to consume backend data. The major difference between HTTP requests and GraphQL is the ability to be specific on querying and/or mutating backend data.

This ability GraphQL has is based of the building of skeletons/structures called **schemas**.

Here is detailed information about these for your consumption:

- [Queries](https://graphql.org/learn/queries/)
- [Mutations](https://graphql.org/learn/queries/#mutations)
- [Schemas](https://graphql.org/learn/schema/)

**Absinthe & Ecto**

These are important Elixir links (database wrapper and package) to GraphQL find more information on the links below. 

- [Ecto](https://hexdocs.pm/ecto/Ecto.html) is Elixir's database wrapper that works around GraphQL.
   
- [Absinthe package](https://hexdocs.pm/absinthe/overview.html) GraphQL toolkit for Elixir.

## **Development**

**GraphiQL Playground**

Visual development with GraphQL, its own integrated development environment (IDE). The GraphiQL playground allows for building and testing queries and mutations.

Open your terminal and run the server command:
```
mix phx.server
```

Once the server is fire up, access the [GraphiQL playground](http://localhost:4000/api/graphiql)
*Note: this URL considers that you are using the built in localhost port for the Phoenix server, which is port 4000. Otherwise this modify the URL to the specific localhost port number.*

**Sample Queries** 

To help you speed up the process of developing/testing using GraphQL, here are some [sample queries and mutations](graphql_doc/sample_queries.md) for you to use on the GraphiQL playground environment.

**Testing**

Always create tests for your GraphQL implementations to ensure code minimize breaking environments. 

## List of Resources

Now that you became familiar with GraphQL and how we use it on our project, here are some other resource you might find interesting. Have fun!

- [GraphQL main documentation](https://graphql.org/learn/)
- [How To GraphQL](https://www.howtographql.com/graphql-elixir/0-introduction/) page

Have fun and hack away!!
