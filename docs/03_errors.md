# Error Codes

## Overview

The API uses standard HTTP status codes and returns detailed error information in the response body.

## HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid or missing token |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 409 | Conflict - Resource already exists |
| 422 | Unprocessable Entity - Validation failed |
| 429 | Too Many Requests - Rate limit exceeded |
| 500 | Internal Server Error |
| 503 | Service Unavailable |

## Error Response Format

All errors return a JSON object:

```json
{
  "error": {
    "code": "invalid_request",
    "message": "The amount field is required",
    "field": "amount"
  }
}
```

## Common Error Codes

### Authentication Errors

| Code | Message | Solution |
|------|---------|----------|
| invalid_token | Token is invalid or expired | Request a new access token |
| missing_auth | Authorization header missing | Include Bearer token in header |
| invalid_credentials | Client ID or secret incorrect | Check your API credentials |

### Payment Errors

| Code | Message | Solution |
|------|---------|----------|
| insufficient_funds | Customer has insufficient funds | Customer needs to add funds |
| card_declined | Card was declined | Customer should try another card |
| invalid_amount | Amount must be positive | Check the amount value |
| duplicate_payment | Payment already exists | Use idempotency key |

### Validation Errors

| Code | Message | Solution |
|------|---------|----------|
| required_field | Field is required | Include the missing field |
| invalid_format | Invalid field format | Check field format requirements |
| value_too_long | Value exceeds maximum length | Shorten the value |

## Rate Limiting

When you exceed rate limits, you'll receive a 429 response:

```json
{
  "error": {
    "code": "rate_limit_exceeded",
    "message": "Too many requests",
    "retry_after": 60
  }
}
```

The `retry_after` field indicates seconds to wait before retrying.

## Idempotency

For POST requests, include an idempotency key to prevent duplicate operations:

```
Idempotency-Key: unique-request-id-123
```

If you retry a request with the same key, you'll get the original response.
