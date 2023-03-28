## Creating resolvers
A resolver is a function. It has the same name as the field that it populates data for. It can fetch data from any data source, then transforms that data into the shape your client requires.

> A resolver's job is to populate the data for a field in your schema. *Your* job is to implement those resolvers.

Each resolver function takes in four parameters: `parent`, `args`, `context`, and `info`. Using these the resolver interacts with our data source.

- `parent` is the returned value of the resolver for this field's parent. This will be useful when dealing with resolver chains.
- `args` is an object that contains all GraphQL arguments that were provided for the field by the GraphQL operation.
- `context` is an object shared across all resolvers that are executing for a particular operation. The resolver needs this context argument to share state, like authentication information, a database connection, or in our case the `RESTDataSource` 
- `info` contains information about the operation's execution state, including the field name, the path to the field from the root, and more.

The order of parameters matters in a resolver function. If you only need to pass in the context you can add an underscore for the parent and two underscores for the args argument but cannot leave them empty.

A best-practice to implement when creating resolvers is to keep them as short as possible which makes your API resilient to future changes and makes code refactoring easier.

## Handling errors
You can face an error in your in your GraphQL query anytime and knowing how to handle these errors can be a great skill to have.

When there is an error always check the query in the Apollo Explorer to see what is the error exactly. `errors` is an array containing each error that occurred as the server tried to execute the query. So yes, there could be multiple errors! `ApolloServer` provides [error codes](https://www.apollographql.com/docs/apollo-server/data/errors/#error-codes) that will help to narrow down what caused the issues.

## GraphQL argument
An argument is a value you provide for a particular field in your query. The schema defines the arguments that each of your fields accepts.

Your resolvers can then use a field's provided arguments to help determine how to populate the data for that field. Arguments can help you retrieve specific objects, filter through a set of objects, or even transform the field's returned value. A query that performs a search usually provides the user's search term as an argument.

To define an argument for a field in our schema, we add parentheses after the field name. Inside, we write the name of the argument followed by a colon, then the type of that argument, like `String` or `Int`. If we have more than one argument, we can separate them with commas.

## Chaining resolvers
GraphQL queries often have nested objects and fields. If we are getting data from multiple endpoints in a single query and a single resolver function won't be able to handle all of this information. For solving this problem we can create a second resolver that gets data from the second endpoint and gives it to the first resolver if it needs it.

>  Resolver chaining is similar to promise chaining in JavaScript.