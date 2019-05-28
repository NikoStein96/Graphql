# Graphql Assignment

### Explain shortly about GraphQL, its purpose and some of its use cases
+ In short, GraphQL is an open source query language created by Facebook Before GraphQL went open source in 2015, Facebook used it internally for their mobile applications since 2012, as an alternative to the common REST architecture.
+ With GraphQL you can query what you need, not more, not less.

### Explain some of the Server Architectures that can be implemented with a GraphQL backend
+ GraphQL server with a connected database
+ GraphQL server that is a thin layer in front of a number of third party or legacy systems and integrates them through a single GraphQL API
+ A hybrid approach of a connected database and third party or legacy systems that can all be accessed through the same GraphQL API
+ All three architectures represent major use cases of GraphQL and demonstrate the flexibility in terms of the context where it can be used.

### What is meant by the terms over- and under-fetching in relation to REST
Over-fetching is fetching too much data, aka there is data in the reponse you don't use.
Under-fetching is not having enough data with a call to an endpoint, leading you to call a second endpoint.

### Explain shortly about GraphQL’s type system and some of the benefits we get from this
GraphQL is a strongly typed language. Type System defines various data types that can be used in a GraphQL application. The type system helps to define the schema, which is a contract between client and server.

### Explain shortly about GraphQL Schema Definition Language, and provide a number of examples of schemas you have defined.
Object Types
Object types are specific to a GraphQL service, are defined with the type keyword and start with a capital letter by convention. They define the type name and the fields present under that type. Each field in an object type can be resolve to either other object types or scalar types. Scalar types point to actual data and represent the leaves of the graph.

In the above schema deffinition we have the Todo object type as well as the Query and Mutation root object types. Only the Query root type is required in all GraphQL schemas, but the mutation root type will most often also be present when the service allows for updating, adding or deleting data. Additionally, a Subscription root type is also available, to define operations that a client can subscribe to.

Built-In Scalar Types
There are 5 built-in scalar types with GraphQL: Int, Float, String, Boolean and ID. Scalar types, as opposed to object types, point to actual data. The ID type resolves to a string, but expects a unique value.

Enumeration Types
Enumeration types allow to define a specific subset of possible values for a type. In the previous example, the Priority enum type can take a value of LOW, MEDIUM or HIGH and anything else will result in a validation error. On the client strings are used to provide a value for an enum type.
```GraphQL
const typeDefs = `
  type Author {
    id: Int!
    firstName: String
    lastName: String
    """
    the list of Posts by this author
    """
    posts: [Post]
  }

  type Post {
    id: Int!
    title: String
    author: Author
    votes: Int
  }

  # the schema allows the following query:
  type Query {
    posts: [Post]
    author(id: Int!): Author
  }

  # this schema allows the following mutation:
  type Mutation {
    upvotePost (
      postId: Int!
    ): Post
  }
  
  ```
