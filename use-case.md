# Use Case: Create and Retrieve Data

This guide demonstrates how a real client application chains multiple API calls together to complete a full user + post creation workflow.

---

## Scenario

A blogging application needs to:

1. Register a new user
2. Confirm the user was created
3. Create a post on behalf of that user
4. Retrieve the post to display it

---

## Workflow Diagram

```
Client App
    │
    ├──① POST /users ──────────► Server creates user, returns userId
    │
    ├──② GET /users/{id} ───────► Server confirms user exists
    │
    ├──③ POST /posts ───────────► Server creates post linked to userId
    │
    └──④ GET /posts?userId=1 ──► Server returns all posts by user
```

---

## Step 1 — Create a User

**Request:**

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

**Response:**

```json
{
  "id": "usr_4829xk",
  "name": "Vishal",
  "email": "vishal@test.com",
  "createdAt": "2026-06-05T10:30:00Z"
}
```

Save the `id` value — you'll use it in Step 3.

---

## Step 2 — Verify the User Exists

**Request:**

```bash
curl -X GET https://api.example.com/users/usr_4829xk \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

**Response:**

```json
{
  "id": "usr_4829xk",
  "name": "Vishal",
  "email": "vishal@test.com",
  "city": "Delhi"
}
```

---

## Step 3 — Create a Post

Use the `userId` returned from Step 1.

**Request:**

```bash
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{
    "title": "My First Post",
    "body": "This is the content of my first post.",
    "userId": 1
  }'
```

**Response:**

```json
{
  "id": 101,
  "title": "My First Post",
  "body": "This is the content of my first post.",
  "userId": 1
}
```

---

## Step 4 — Retrieve Posts by User

**Request:**

```bash
curl -X GET "https://jsonplaceholder.typicode.com/posts?userId=1" \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

**Response:**

```json
[
  {
    "userId": 1,
    "id": 101,
    "title": "My First Post",
    "body": "This is the content of my first post."
  }
]
```

---

!!! success "Workflow complete"
    The client has successfully created a user, confirmed the account, published a post, and retrieved it — all using chained API calls.

---

## Key Takeaways

- Always store the `id` from a POST response before making further related requests
- Use GET requests to confirm resources were created before proceeding
- Bearer Tokens must be included on every call in the chain
