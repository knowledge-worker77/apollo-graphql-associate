## Working with real data
Now that we know about how a GraphQL query actually works we can answer these questions to make our app even better.

- Where is our data stored, and how is it structured?
- Is that structure different from our client app's needs and schema?
- How can our resolver functions access that data?

The data that revolvers retrieve can come from all kinds of places: a database, a third-party API, web-hooks, and so on. 

These are called **data sources**. The beauty of GraphQL is that you can mix any number of data sources to create an API that serves the needs of your client app.

## Apollo data source
The GraphQL server can access the REST-API using the traditional `fetch` method or it can use a helper class called `DataSource` which is provided by Apollo.

The data-source class takes care of a few challenges and limitations that come with the direct approach.

The reason that the data-source class is better than fetch is that it doesn't create the N+1 problem which is a very common problem that can happen when working with GraphQL and APIs in general.

Suppose we have 100 blog posts and all of them written by the same author. The fetch method would have made 101 API calls to get all of the blog posts and authors because the author's details are at a different endpoint then the blogs.

Using the data-source class we need only two API calls to get all of our data from the server.