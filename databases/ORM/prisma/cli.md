```bash
# This command created a new directory called prisma which contains 
# a file named schema.prisma and a .env file in the root of the project.
# schema.prisma contains the Prisma schema with your database connection 
# and the Prisma Client generator. .env is a dotenv file for defining 
# environment variables (used for your database connection).
npx prisma init

# This command does two things:
#  - It creates a new SQL migration file for this migration
#  - It runs the SQL migration file against the database
npx prisma migrate dev --name init
```