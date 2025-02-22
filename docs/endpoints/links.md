---
title: Links
sidebar_position: 3
---

This page contains information about the `/links` endpoint, which is used to manage your links.

## Get a link

Get a link by its ID.

### Request

`:id` is the ID of the link you want to get.

```http request
GET /api/links/:id
```

### Example Response

```json
{
  "id": "bd0e4bc2-f7ef-460a-a99e-f4976535d540",
  "type": "last.fm",
  "value": "ItsYuuto"
}
```

## Create a link

Create a new link.

### Request

```http request
POST /api/links
Content-Type: application/json
```

Example body:
```json
{
  "type": "steam",
  "value": "id/PasYuuto"
}
```

### Example Response

Returns a 201 status on success, and the link object in the response body.

```json
{
  "id": "5675e563-0fd3-419b-947f-d95e507f673b",
  "type": "steam",
  "value": "id/PasYuuto"
}
```

## Delete a link

Delete a link by its ID.

### Request

`:id` is the ID of the link you want to delete. Obviously, you can only delete your own links.

```http request
DELETE /api/links/:id
```

### Example Response

Returns:
* a 204 status on success.
* a 404 status if the link does not exist.
* a 403 status if the link does not belong to you.