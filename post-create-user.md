# POST /users

Creates a new user account. Accepts user details in the request body and returns the created user with a server-generated unique ID.

---

## Endpoint

```
POST https://api.example.com/users
```

---

## Request Headers

| Header | Value | Required |
|---|---|---|
| `Content-Type` | `application/json` | Yes |
| `Authorization` | `Bearer YOUR_API_TOKEN` | Yes |

---

## Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| `name` | string | Yes | Full name of the user |
| `email` | string | Yes | Valid email address |
| `city` | string | No | City where the user is located |

---

## Example Request

```bash
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{
    "name": "Vishal",
    "email": "vishal@test.com",
    "city": "Delhi"
  }'
```

---

## Example Response

```json
{
  "id": "usr_4829xk",
  "name": "Vishal",
  "email": "vishal@test.com",
  "city": "Delhi",
  "createdAt": "2026-06-05T10:30:00Z"
}
```

---

## Response Fields

| Field | Type | Description |
|---|---|---|
| `id` | string | Server-generated unique user ID |
| `name` | string | Name of the created user |
| `email` | string | Email of the created user |
| `city` | string | City of the user |
| `createdAt` | string (ISO 8601) | Timestamp when the user was created |

---

## Status Codes

| Code | Meaning |
|---|---|
| `201 Created` | User successfully created |
| `400 Bad Request` | Missing required fields or invalid email format |
| `401 Unauthorized` | Invalid or missing token |
| `409 Conflict` | A user with this email already exists |
