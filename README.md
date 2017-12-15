# GraphQL Server Example

> NOTE: This example currently doesn't work. Expect some fixes shortly.

This example illustrates the usage of the GraphQL Gateway pattern with graphql.js and Graphcool.

**Theme**: This is an example app implementing a minimal version of Airbnb.

## Getting Started ([Hosted demo](https://airbnb.now.sh))

### Initializing the Graphcool Database Service

```sh
cd database
graphcool deploy # copy the service id into the `GRAPHCOOL_SERVICE_ID` env var in .env
graphcool root-token apikey # put the root token into the `GRAPHCOOL_TOKEN` env var in .env
```

### Starting the Server

```sh
yarn install
yarn start
# Open http://localhost:5000/
```

### Seeding some data

```sh
# Runs seed mutations in queries/seed.graphql
yarn seed
```

### Booking flow
Look in `queries/booking.graphql` to see the booking flow.

## Stack

* [`graphql-yoga`](https://github.com/graphcool/graphql-yoga): GraphQL HTTP & subscription server
* [`graphql-remote`](https://github.com/graphcool/graphql-remote): Schema stitching helper library
* [`graphcool`](https://github.com/graphcool/framework): GraphQL database
* [`now`](https://zeit.co/now): Server deployment

## Architecture

```
                          +-----------+    +--------------------------+
                          |           |    |                          |
                          |           +----+  Graphcool (GraphQL DB)  |
+--------------------+    |           |    |                          |
|                    |    |  GraphQL  |    +--------------------------+
|   GraphQL Client   +----+    API    |
|                    |    |  Server   |    +--------------------------+
+--------------------+    |           |    |                          |
                          |           +----+     Legacy Rest API      |
                          |           |    |                          |
                          +-----------+    +--------------------------+
```

## Project structure

### Directories

* `database`: GraphQL database service definitions (using Graphcool)
* `queries`: Helpful GraphQL queries and mutations to seed data and demo the app
* `schemas`: Generated GraphQL schemas of the database service & gateway
* `src`: Source code of the gateway

### Files

* `.env`: Contains env vars (such as `GRAPHCOOL_SERVICE_ID` and `GRAPHCOOL_TOKEN`)
* `.graphqlconfig`: [GraphQL config](https://github.com/graphcool/graphql-config) file used for IDE support and [`graphql-cli`](https://github.com/graphcool/graphql-cli)
* `tsconfig.json`: Typescript compiler settings

## License
MIT
