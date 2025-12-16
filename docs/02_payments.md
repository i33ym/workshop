# Payments

## Overview

The Payments API allows you to create, retrieve, and manage payment transactions.

## Creating a Payment

To create a new payment, make a POST request:

```
POST /api/v1/payments
```

### Request Body

```json
{
  "amount": 10000,
  "currency": "UZS",
  "description": "Order #12345",
  "merchant_id": "merchant_abc123",
  "callback_url": "https://yoursite.com/webhook",
  "return_url": "https://yoursite.com/success"
}
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| amount | integer | Yes | Amount in smallest currency unit (tiyin for UZS) |
| currency | string | Yes | Three-letter currency code (UZS, USD) |
| description | string | No | Payment description |
| merchant_id | string | Yes | Your merchant identifier |
| callback_url | string | Yes | URL for webhook notifications |
| return_url | string | No | URL to redirect after payment |

### Response

```json
{
  "id": "pay_123456789",
  "status": "pending",
  "amount": 10000,
  "currency": "UZS",
  "payment_url": "https://checkout.example.com/pay/abc123",
  "created_at": "2024-01-15T10:30:00Z"
}
```

## Retrieving a Payment

Get details of an existing payment:

```
GET /api/v1/payments/{payment_id}
```

### Response

```json
{
  "id": "pay_123456789",
  "status": "completed",
  "amount": 10000,
  "currency": "UZS",
  "completed_at": "2024-01-15T10:35:00Z"
}
```

## Payment Statuses

| Status | Description |
|--------|-------------|
| pending | Payment created, awaiting customer action |
| processing | Payment is being processed |
| completed | Payment successful |
| failed | Payment failed |
| cancelled | Payment cancelled by customer |
| refunded | Payment has been refunded |

## Cancelling a Payment

Cancel a pending payment:

```
POST /api/v1/payments/{payment_id}/cancel
```

Returns the updated payment object with status "cancelled".
