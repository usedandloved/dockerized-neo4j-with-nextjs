# Welcome

This project is a simple example of how to work with [Neo4j](https://neo4j.com) within a [Docker](https://www.docker.com) container.

All you need to have installed on your system to run this example is [Docker](https://www.docker.com).

If you do not have [Docker](https://www.docker.com) installed on your development system, you can download and install the freely available [Docker Desktop](https://www.docker.com/products/docker-desktop).

## Getting started

To spin up your Dockerized Neo4j and Next.js project:

```sh
# Use the existing Docker images on your system
$ npm run dev

# OR #

# Force a clean build to ensure your instances are using the latest code
$ npm run dev:clean
```

### Neo4j

Once you have started your Dockerized project, you can access the Neo4j Browser at [http://localhost:7474/browser/](http://localhost:7474/browser/) - using the following credentials:

- Username: `neo4j`
- Password: `letmein`

![neo4j/v4.x.x/__screenshots__/neo4j-browser-login.png](neo4j/v4.x.x/__screenshots__/neo4j-browser-login.png)

Once you've logged in, you are free to explore your Dockerized Neo4j instance.

![neo4j/v4.x.x/__screenshots__/neo4j-browser-example.png](neo4j/v4.x.x/__screenshots__/neo4j-browser-example.png)

#### OPTIONAL: Use Cypher text file(s) to seed your database

If you would like to have your database load a pre-defined series of Cypher commands - such as the example at `neo4j/v4.x.x/__seed__/db.cypher` - simply uncomment the following in `neo4j/v4.x.x/Dockerfile`:

```sh
# neo4j/v4.x.x/Dockerfile

...
# COPY ./__seed__/*.cypher /var/lib/neo4j/import/
...

```

This will ensure that your Cypher file(s) are copied and then processed by the `neo4j/v4.x.x/wrapper.sh` script when building your Neo4j instance.

### Next.js

An example [Next.js](https://nextjs.org) application has been created so that we can leverage the [Neo4j GraphQL Library](https://neo4j.com/docs/graphql-manual/current/).

Once you have started your Dockerized project, you can access the Next.js GraphQL API at [http://localhost:3000/api/graphql](http://localhost:3000/api/graphql)

#### EXAMPLE: Create a query to verify our GraphQL API is online

Let's use the `ping` query that we have defined in our GraphQL schema:

```gql
{
  ping {
    message
    timestamp
  }
}
```

You should see a response similar to:

```json
{
  "data": {
    "ping": {
      "message": "Pong",
      "timestamp": "2021-09-05T02:05:52.000Z"
    }
  }
}
```

### Resources

If you are looking for a great overview on setting up a Next.js GraphQL API, I strongly recommend William Lyon's [blog post](https://www.lyonwj.com/blog/graphql-server-next-js-neo4j-aura-vercel) at [https://www.lyonwj.com/blog/graphql-server-next-js-neo4j-aura-vercel](https://www.lyonwj.com/blog/graphql-server-next-js-neo4j-aura-vercel).
