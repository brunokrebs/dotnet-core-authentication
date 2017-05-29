## Interacting with the API

Adding a new to do item:

```bash
curl -H "Content-Type: application/json" -X POST -d '{
    "name": "my first incomplete task",
    "isComplete": false
}'  http://localhost:5000/api/todo
```

Listing all items:

```bash
curl http://localhost:5000/api/todo
```

Delete item with id = 2:

```bash
curl -X DELETE http://localhost:5000/api/todo/2
```

## Auth

NuGet dependencies:

```bash
dotnet add package JWT -v 3.0.0-beta4
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```

Registering a new user:

```bash
curl -H "Content-Type: application/json" -X POST -d '{
    "email": "bruno.krebs@auth0.com",
    "password": "123bruno"
}'  http://localhost:5000/api/account
```

Signing in and keeping access token on an env variable:

```bash
ACCESS_TOKEN="$(curl -H "Content-Type: application/json" -X POST -d '{
    "email": "bruno.krebs@auth0.com",
    "password": "123bruno"
}'  http://localhost:5000/api/account/sign-in | jq -r '.access_token')"
```

Using the `ACCESS_TOKEN` env variable to get all To Do items.

```bash
curl -H "Authorization: Bearer $ACCESS_TOKEN" http://localhost:5000/api/todo
```
