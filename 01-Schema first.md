## Schema first approach
In a schema-first approach we first identify the features that our app will need and create our schema based on those requirements. 

A schema-first design minimizes the development type as both the front and back-end teams can work on the project in parallel.

## Gathering required  data
Before we can create the schema we need to gather data about each of the features that our app will have. In most cases you can gather data from the requirements that the client provided.

## Introduction to the GraphQL schema
A **schema** is like a contract between the server and the client. It defines what a GraphQL API can and can't do, and how clients can request or change data.
It's an abstraction layer that provides flexibility to consumers while hiding back-end implementation details.

> GraphQL provides it's own language to define schemas called schema definition language or SDL for short.

A schema is a collection of objects and each object can have a field. This is kinda like how objects work in JavaScript. Each field has a type which can either be a scalar (String, Integer, etc…) or we can define the type our selves.

we can use the `type` keyword to define a new type definition in our schema. The `Query` is a special type of object in a GraphQL schema that allows us to retrieve the data from the back-end API or database.

Queries are considered entry-points into the schema that the front-end can use to query data.