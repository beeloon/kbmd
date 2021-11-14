# [Connection URLs](https://www.prisma.io/docs/reference/database-reference/connection-urls)
Prisma needs a connection URL to be able to connect to your database, e.g. when sending queries with Prisma Client or when changing the database schema with Prisma Migrate.

The connection URL is provided via the url field of a datasource block in your Prisma schema. It generally consists of the following components (except for SQLite):
 - User: The name of your database user
 - Password: The password for your database user
 - Host: The IP or domain name of the machine where your database server is running
 - Port: The port on which your database server is running
 - Database name: The name of the database you want to use

## Example
Here are examples for the connection URLs of the databases Prisma supports:

### PostgreSQL
```prisma
datasource db {
  provider = "postgresql"
  url      = "postgresql://janedoe:mypassword@localhost:5432/mydb"
}
```

### .env
You can also provide the connection URL as an environment variable:

```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```