# API Documentation

This directory contains API documentation for Horizon modules and services.

## Overview

API documentation provides detailed information about:
- REST API endpoints
- Request/response formats
- Authentication and authorization
- Rate limiting
- Error handling
- API versioning

## Structure

API documentation can be organized by:

- **Service**: One directory per service (e.g., `user-service/`, `auth-service/`)
- **Version**: Versioned API docs (e.g., `v1/`, `v2/`)
- **Resource**: Organized by resource type (e.g., `users.md`, `projects.md`)

## Documentation Format

Each API document should include:

### Endpoint Documentation

```markdown
## POST /api/v1/resource

Description of what this endpoint does.

### Request

**Headers:**
- `Authorization: Bearer <token>` (required)
- `Content-Type: application/json` (required)

**Body:**
```json
{
  "field1": "value1",
  "field2": "value2"
}
```

**Parameters:**
- `field1` (string, required): Description
- `field2` (string, optional): Description

### Response

**Success (200 OK):**
```json
{
  "id": "123",
  "status": "success"
}
```

**Error (400 Bad Request):**
```json
{
  "error": "Invalid request",
  "message": "field1 is required"
}
```

### Example

```bash
curl -X POST https://api.example.com/api/v1/resource \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"field1": "value1"}'
```
```

## Authentication

If your APIs require authentication, create an `authentication.md` file documenting:
- Authentication methods (API keys, OAuth, JWT, etc.)
- How to obtain credentials
- How to include credentials in requests
- Token expiration and refresh

## Error Codes

Create an `error-codes.md` file listing:
- HTTP status codes used
- Error response format
- Common error scenarios
- Troubleshooting steps

## Rate Limiting

Document rate limiting policies:
- Request limits per time period
- Rate limit headers
- What happens when limits are exceeded
- Best practices for handling rate limits

## Contributing

When adding API documentation:

1. Create a clear, descriptive filename
2. Include all endpoints for that API
3. Provide complete request/response examples
4. Document all error cases
5. Add authentication requirements
6. Link from relevant module documentation
7. Follow the [Style Guide](../guides/STYLE_GUIDE.md)

## Tools

Consider using these tools for API documentation:
- **OpenAPI/Swagger**: For REST APIs
- **GraphQL Schema**: For GraphQL APIs
- **Postman Collections**: For testing and examples
- **API Blueprint**: For API design

## Related Documentation

- [Module Documentation](../modules/)
- [Style Guide](../guides/STYLE_GUIDE.md)
- [Architecture Documentation](../architecture/)
