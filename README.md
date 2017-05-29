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

```bash
dotnet add package JWT -v 3.0.0-beta4
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```
