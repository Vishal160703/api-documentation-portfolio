# GET /posts

Retrieves a list of posts from the server. Returns all posts by default, or a filtered result when query parameters are provided.

---

## Endpoint

```
GET https://jsonplaceholder.typicode.com/posts
```

---

## Request Headers

| Header | Value | Required |
|---|---|---|
| `Content-Type` | `application/json` | Yes |
| `Authorization` | `Bearer YOUR_API_TOKEN` | Yes |

---

## Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `id` | integer | No | Filter posts by ID. Example: `?id=1` |

---

## Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `{id}` | integer | No | Retrieve a single post. Example: `/posts/1` |

---

## Example Requests

=== "Get all posts"

    ```bash
    curl -X GET https://jsonplaceholder.typicode.com/posts \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer YOUR_API_TOKEN"
    ```

=== "Filter by ID"

    ```bash
    curl -X GET "https://jsonplaceholder.typicode.com/posts?id=1" \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer YOUR_API_TOKEN"
    ```

=== "Get single post"

    ```bash
    curl -X GET https://jsonplaceholder.typicode.com/posts/1 \
      -H "Content-Type: application/json" \
      -H "Authorization: Bearer YOUR_API_TOKEN"
    ```

---

## Example Response

```json
[
  {
    "userId": 1,
    "id": 1,
    "title": "Sample Title",
    "body": "Sample content describing the post in detail."
  }
]
```

---

## Response Fields

| Field | Type | Description |
|---|---|---|
| `userId` | integer | ID of the user who created the post |
| `id` | integer | Unique identifier of the post |
| `title` | string | Title of the post |
| `body` | string | Full content of the post |

---

## Status Codes

| Code | Meaning |
|---|---|
| `200 OK` | Request successful, posts returned |
| `401 Unauthorized` | Invalid or missing token |
| `404 Not Found` | Post ID does not exist |
