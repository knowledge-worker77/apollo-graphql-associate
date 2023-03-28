## Apollo server and client
When working on the back-end of your application with GraphQL your main objectives should be to create a server that can handle these things:

- Receive an incoming GraphQL query from our client
- Validate that query against our newly created schema
- Populate the queried schema fields with mocked data
- Return the populated fields as a response

Apollo provides the `Apollo Server` library to implement all of these features in our server easily. If the front-end of your application has not been created yet then you can use mock data to test your queries.

Apollo also provides us an in-browser IDE of sorts to test and validate or GraphQL queries kind of like using postman for REST. The in-browser IDE is called `Apollo Explorer` and is available at `localhost:4000` . The Explorer is free to use, and it provides awesome development features like interactive query building, query history, and response hints. This will make building our queries fast and fun.

For the front-end of your application Apollo provides the `Apollo Client` library which is used to execute queries from the front-end. It also provides it's own in-memory cache so that each request after the first one will be executed immediately unless the data has been changed from the server.

## Executing queries
If you're using React for building your front-end application then Apollo provides a `useQuery` hook for executing queries from a React application.

The `useQuery` hook is the primary API for executing queries in a React application. We run a query within a React component by calling `useQuery` and passing it our GraphQL query string.

This makes running queries from React components a breeze. When our component renders, `useQuery` returns an object from Apollo Client that contains `loading`, `error`, and `data` properties that we can use to render our UI.

## Client-side queries
Our client app needs to fetch data from the server and then display it on the web page.

The client can either send a `GET` or `POST` request to the server depending on the query that we tell the client to send.

The server receives the request from the client and it parses the information from the request into a tree-structured document called an `AST` (Abstract Syntax Tree). With this, the server validates the query against the types and fields in our schema. If anything is wrong then the server gives an error and does not validate the request.

When the server is done resolving all the fields of the query it assembles all the required data into an JSON object which is the same as the query. The JSON object is then added to the request's data key. and then returned to the client.

The client receives this data and adds it to the required components and then displays them to the user.

## Creating queries
The Apollo Explorer provides us with a schema page that lists all the details about our schema. The schema page has two main sections: Reference and SDL.

- The *SDL* tab shows you your schema represented in schema definition language. It should look familiar from your own.
- The *Reference* tab shows you a high-level overview of your schema, including its defined types and fields.

## Validating queries
The `$` symbol in a GraphQL query represents a variable which we can use throughout the query. After the colon is the variable's type, which must match the type of the argument we'll use it for. Variables are used to pass dynamic arguments that we can modify from the front-end of our application.