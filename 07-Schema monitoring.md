## GraphQL introspection
Introspection is a GraphQL feature that enables us to query a GraphQL server for information about the underlying schema. This includes data like types, fields, and field-level descriptions. Tools like Apollo Sandbox use introspection to build and run queries.

Introspection can cause a huge problem when it comes to the security of our graph because it exposes all of our graph's structure and what we can do with it to the whole world. As safety precaution, Apollo Server disables introspection by default in a production environment.
## Monitoring field usage
The *Fields* page in the Apollo Studio gives a small overview about the fields in our schema. It mainly shows us two metrics:

- **Field executions** represents how many times the server has executed the resolver function for a specific field over the given period.
- **Referencing operations** lists the number of operations in a given period that have *included* the particular field.

## Deprecating fields
When your graph starts to evolve it will undergo both major and minor changes and sometimes you'll even have to remove some fields that exist in your schema. You can't remove a field without giving a warning to the users and other developers that use your schema in their GraphQL APIs.

The best solution is to deprecate the field and add a new one in it's place. GraphQL provides the `@depricated` directive to tell the server that this field is now deprecated and will be removed in the upcoming versions.

You also need to provide a reason as to why the field has been deprecated and which is the new field that will replace it.

## Monitoring and scaling
The *operations* page in Apollo Studio allows us to see an overview of our request rate, service time, and error percentage, including specific operations for each of these that might be worth drilling deeper into.
