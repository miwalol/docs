---
title: Shop
sidebar_position: 5
---

This page contains information about the `/shop` endpoint.

## Get owned items

Get all items that the authenticated user owns.

### Request

```http request
GET /api/shop/owned
```

Optional query parameters:
* `type` - Filter items by type. Possible values: `avatar_decoration`.

### Example Response

```json
[
  {
    "id": "a13bdc64-fd4a-4226-a696-2d5276406ae2",
    "type": "avatar_decoration",
    "name": "Crown",
    "description": "A crown for your avatar.",
    "price": 5.00, // Price in Euros
    "expires_at": null // Expiration date, if any
  }
  // ...
]
```