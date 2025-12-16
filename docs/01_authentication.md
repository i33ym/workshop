# Authentication

## Overview

All API requests require authentication using a Bearer token. This token must be included in the Authorization header of every request.

## Getting an Access Token

To obtain an access token, make a POST request to the authentication endpoint:

```
POST /api/v1/auth/token
```

### Request Body

```json
{
  "client_id": "your_client_id",
  "client_secret": "your_client_secret"
}
```

### Response

```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIs...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

## Using the Token

Include the token in the Authorization header:

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

## Token Expiration

Access tokens expire after 1 hour (3600 seconds). When a token expires, you must request a new one.

## Refresh Tokens

For long-lived sessions, use refresh tokens:

```
POST /api/v1/auth/refresh
```

```json
{
  "refresh_token": "your_refresh_token"
}
```

## Security Best Practices

1. Never expose your client_secret in client-side code
2. Store tokens securely
3. Use HTTPS for all API calls
4. Rotate secrets periodically
