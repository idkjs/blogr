# prisma endpoints

* HTTP: https://eu1.prisma.sh/alain-armand-1b1a62/blogr/dev
* WS: wss://eu1.prisma.sh/alain-armand-1b1a62/blogr/dev

# prisma token

* run `prisma token` in /database and add to playground http headers and reload.

```json
{
  "Authorization":
    "Bearer eyJhbGciOiJIUzI1NiIsInR5example.eyJkYXRhIjp7InNlcnZpY2UiOiJibG9nckBkZXYiLCJyb2xlcyI6WyJhZG1pbiJdfSwiaWF0IjoxNTE5OTA4NzQ3LCJleHAiOjE1MjA1MTM1NDd9.KBFiqollloh49MRSGVl3J2i-dhS0EabwWjEXAMPLE"
}
```

# TAKEAWAYS

## Work with app graphql api and prisma generated api side by side

* If you download the standalone version of the GraphQL Playground, you can work with the API of your graphql-yoga server and the Prisma API side-by-side (run prisma playground after you downloaded and installed it on your machine). The projects are read from the .graphqlconfig.yml file as well.

* This didn't work because .yml format was wrong and playground could not read the endpoint on localhost:4000. .yml reads indentation so the following didnt work:

```yml
projects:
  database:
    schemaPath: src/generated/prisma.graphql
    extensions:
      prisma: database/prisma.yml
  app:
    schemaPath: src/schema.graphql
    extensions:
      endpoints:
  default: http://localhost:4000
```

* proper indentation for default endpoint:

```yml
projects:
  database:
    schemaPath: src/generated/prisma.graphql
    extensions:
      prisma: database/prisma.yml
  app:
    schemaPath: src/schema.graphql
    extensions:
      endpoints:
        default: http://localhost:4000
```
