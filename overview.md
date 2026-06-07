# Posts API – Overview

The Posts API allows client applications to create, retrieve, update, and delete post content. It is commonly used in blogging platforms, news feeds, and content management systems.

---

## Base URL

```
https://jsonplaceholder.typicode.com
```

---

## Available Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/posts` | Retrieve all posts or filter by ID |
| `GET` | `/posts/{id}` | Retrieve a single post by ID |
| `POST` | `/posts` | Create a new post |

---

## Authentication

All requests require a **Bearer Token** in the `Authorization` header.

```
Authorization: Bearer YOUR_API_TOKEN
```

See the [Authentication Guide](../guides/authentication.md) for full details.

---

## Response Format

All responses are returned in **JSON** format.

```
Content-Type: application/json
```

---

## Error Handling

Refer to the [Error Reference](errors.md) for a full list of HTTP status codes and error response examples.
