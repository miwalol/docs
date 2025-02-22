---
title: Cards
sidebar_position: 2
---

This page contains information about the `/cards` endpoint, which is used to manage your cards.

:::info

This endpoint requires authentication and the [`cards` scope](/auth/scopes#cards).

:::

## Get a card

Get a card by its ID.

### Request

`:id` is the ID of the card you want to get.

```http request
GET /api/cards/:id
```

### Example Response

```json
{
  "id": "d1d882ad-b78b-4164-81e3-b1feafe59460",
  "type": "server",
  "value": "https://discord.gg/miwa"
}
```

:::caution

For type `discord`, the `value` field will be `null`.

:::

## Create a card

Create a new card.

### Request

```http request
POST /api/cards
Content-Type: application/json
```

Example body:
```json
{
  "type": "server",
  "value": "https://discord.gg/miwa"
}
```

### Example Response

Returns a 201 status on success, and the card object in the response body.

```json
{
  "id": "d1d882ad-b78b-4164-81e3-b1feafe59460",
  "type": "server",
  "value": "https://discord.gg/miwa"
}
```

## Delete a card

Delete a card by its ID.

### Request

`:id` is the ID of the card you want to delete. Obviously, you can only delete your own cards.

```http request
DELETE /api/cards/:id
```

### Example Response

Returns:
* a 204 status on success.
* a 404 status if the card does not exist.
* a 403 status if the card does not belong to you.