## The schema registry
Our app, along with our schema, is intended to evolve over time as we add new features and improve our code-base. To support this healthy schema evolution, we can use the Apollo **schema registry**.

The schema registry is a version control system for our schema. It stores our schema's change history, tracking the types and fields that were added, modified, and removed. The registry powers almost every Apollo feature.

The repository is similar to how GitHub and Git work. Thanks to the schema registry, we can track variants of the same graph that are deployed in different environments, such as staging and production.

We can run schema checks to detect when a potential change might break one of our clients. We can also use the Explorer on a production graph without relying on introspection, so our graph's structure is kept private from unauthorized clients.

As our graph grows, multiple teams might even want to break parts of it into separate sub-graphs that they manage independently. The schema registry can take care of tracking all those sub-graphs, enabling Apollo to surface potential conflicts between them, and even powering schema composition with Apollo federation

## Registering our schema
If you want to put your GraphQL application into a production environment then you need to first register your schema with Apollo.

> You will require a Apollo account that is setup by an organization.

To register a schema deployed in production, we need to create a deployed graph, which integrates with the schema registry. 

A deployed graph is visible to all members of your organization. To create a new graph click on the `New Graph` button and follow the prompts as per your requirements.

## Deploying the server
The tutorial uses `Heroku` to deploy the server because it can sync changes from a Git repository easily. It also provides two ways how you can setup your deploys.

- Automatic deploys will deploy new changes made to your server whenever you push a Git commit.
- Manual deploys will deploy new changes only when you click on the `Deploy branch` from your heroku dashboard.

## Deploying the Client
Deploying the client application used in the tutorial is very simple. You just make the  changes that you require and deploy it on the server-platform like you deployed the server.