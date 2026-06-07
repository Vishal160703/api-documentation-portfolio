# Error Reference

All API errors follow a consistent JSON structure. This page lists all possible HTTP status codes and their meanings.

---

## Error Response Format

```json
{
  "error": "A human-readable description of the error"
}
```

---

## HTTP Status Codes

| Status Code | Name | Description |
|---|---|---|
| `200` | OK | Request was successful |
| `201` | Created | Resource was successfully created |
| `400` | Bad Request | The request was malformed or missing required fields |
| `401` | Unauthorized | The Bearer Token is missing or invalid |
| `403` | Forbidden | You do not have permission to access this resource |
| `404` | Not Found | The requested endpoint or resource does not exist |
| `409` | Conflict | A resource with the same identifier already exists |
| `422` | Unprocessable Entity | Request body is valid JSON but contains invalid field values |
| `500` | Internal Server Error | An unexpected error occurred on the server |

---

## Error Examples

=== "400 Bad Request"

    ```json
    {
      "error": "Invalid email format"
    }
    ```

=== "401 Unauthorized"

    ```json
    {
      "error": "Authorization token is missing or expired"
    }
    ```

=== "404 Not Found"

    ```json
    {
      "error": "Post with ID 999 not found"
    }
    ```

=== "500 Server Error"

    ```json
    {
      "error": "An internal server error occurred. Please try again later."
    }
    ```

---

!!! tip "Debugging tip"
    Always check the `error` field in the response body — it provides a specific reason beyond the HTTP status code, which is useful for debugging.
