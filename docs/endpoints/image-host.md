---
title: Image Host
sidebar_position: 6
---

This page contains information about the `/imagehost` endpoint, which is used to upload and manage images to the Image Host.

:::info

The Image Host is a **paid feature**. The authenticated user must have an active subscription to use this endpoint.

:::

## Upload an image

Upload an image to the Image Host.

### Request

```http request
POST /api/imagehost/upload
Content-Type: multipart/form-data

file: <image>
```

### Example Response

Returns a 201 status on success, and the image URL in the response body.

```json
{
  "url": "https://i.miwa.lol/63c33bef-f525-48f2-9372-1426901caa56.png"
}
```

## Delete an image

Delete an image from the Image Host.

### Request

```http request
DELETE /api/imagehost/{image_id}
```

### Example Response

Returns:
* a 204 status on success.
* a 404 status if the image doesn't exist.
* a 403 status if the image doesn't belong to you.