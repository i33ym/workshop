# Webhooks

## Overview

Webhooks allow you to receive real-time notifications when events occur in your account. Instead of polling the API, we'll send HTTP POST requests to your server.

## Setting Up Webhooks

Configure your webhook URL in the dashboard or via API:

```
POST /api/v1/webhooks
```

```json
{
  "url": "https://yoursite.com/webhooks",
  "events": ["payment.completed", "payment.failed", "refund.created"]
}
```

## Event Types

| Event | Description |
|-------|-------------|
| payment.created | A new payment was created |
| payment.completed | Payment was successful |
| payment.failed | Payment failed |
| payment.cancelled | Payment was cancelled |
| refund.created | A refund was initiated |
| refund.completed | Refund was successful |

## Webhook Payload

All webhooks have this structure:

```json
{
  "id": "evt_123456789",
  "type": "payment.completed",
  "created_at": "2024-01-15T10:35:00Z",
  "data": {
    "id": "pay_123456789",
    "amount": 10000,
    "currency": "UZS",
    "status": "completed"
  }
}
```

## Verifying Webhooks

Each webhook includes a signature header for verification:

```
X-Webhook-Signature: sha256=abc123...
```

Verify the signature using your webhook secret:

```python
import hmac
import hashlib

def verify_webhook(payload, signature, secret):
    expected = hmac.new(
        secret.encode(),
        payload.encode(),
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(f"sha256={expected}", signature)
```

## Responding to Webhooks

Your endpoint must return a 200 status code within 30 seconds.

If we don't receive a 200 response, we'll retry:
- After 1 minute
- After 5 minutes
- After 30 minutes
- After 2 hours
- After 24 hours

## Best Practices

1. **Respond quickly** - Process webhooks asynchronously
2. **Handle duplicates** - Use the event ID for idempotency
3. **Verify signatures** - Always verify webhook authenticity
4. **Use HTTPS** - Webhook URLs must use HTTPS
5. **Log everything** - Keep records for debugging

## Testing Webhooks

Use the test endpoint to simulate events:

```
POST /api/v1/webhooks/test
```

```json
{
  "event_type": "payment.completed",
  "webhook_id": "wh_123"
}
```
