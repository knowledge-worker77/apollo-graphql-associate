## GraphQL mutations
We used queries in GraphQL for reading our data. If we want to write data or modify data from the client we use `mutations`.

Much like the `Query` type, the `Mutation` type serves as an entry point to our schema. It follows the same syntax as the schema definition language, or SDL. We declare the `Mutation` type using the `type` keyword, then the name `Mutation`.

Inside the curly braces, we have our entry points, the fields we'll be using to mutate our data.

When we use a mutation to modify more than object we return all of the objects that are modified to show that the mutation has been successful.

## Resolving mutations
Mutations are defined just like queries are. We will add a mutation resolver inside the mutation object which also needs to have the same name as in our schema. We can put the mutation in a try-catch block to easily handle any errors that we might face.

We can also be more dynamic and use the values that Apollo Server and the `RESTDataSource` class provide. When an error occurs, Apollo Server attaches an `extensions` field to that error that contains relevant error details.

## Building a mutation
We start with the `mutation` keyword, and then the name of the operation (Adding a verb like add or delete is really helpful when creating mutations.) You can use variables to filter when updating specific data.

## The useMutation hook
When we want to execute the mutation from our front-end application we can use the `useMutation` hook that Apollo provides us. Unlike with `useQuery`, calling `useMutation` doesn't actually execute the mutation automatically. Instead, the `useMutation` hook returns an array with two elements.

- The first element is the **mutate function** we'll use to actually run the mutation later on.
- The second element is an object with information about the mutation: `loading`, `error` and `data`.

You can use an `onClick` method or any other way you want to trigger the mutation when you want to update data from a GraphQL API.