# Authentication

All API requests in this portfolio use **Bearer Token authentication**. This page explains what it is, how to use it, and common errors.

---

## What is Bearer Token Authentication?

A Bearer Token is a security credential passed in the `Authorization` header of every API request. The server uses this token to verify the identity and permissions of the caller before processing the request.

Bearer tokens are the most common authentication method for REST APIs and are used by services like GitHub, Stripe, and Paytm.

---

## How to Pass the Token

Add the following header to every request:

```
Authorization: Bearer YOUR_API_TOKEN
```

### Example (cURL)

```bash
curl -X GET https://api.example.com/posts \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
```

### Example (Postman)

1. Open your request in Postman
2. Go to the **Authorization** tab
3. Select **Bearer Token** from the type dropdown
4. Paste your token in the **Token** field
5. Postman automatically adds the `Authorization` header

---

## Token Format

Tokens in this API are **JWT (JSON Web Tokens)**. A typical token looks like:

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiIxMjMiLCJpYXQiOjE2MDAwMDAwMDB9.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

It has three parts separated by dots: **header**, **payload**, and **signature**.

---

## Common Authentication Errors

| Error | Cause | Fix |
|---|---|---|
| `401 Unauthorized` | Token is missing or expired | Regenerate your token and retry |
| `403 Forbidden` | Token is valid but lacks permission | Use a token with correct scope/role |

!!! warning
    Never share your Bearer Token publicly or commit it to a GitHub repository. Use environment variables or a secrets manager to store tokens securely.
