---
title: Uploads
sidebar_position: 4
---

This page contains information about the `/upload` endpoint, which is used to upload avatars, backgrounds, audios, custom cursors, and custom fonts.

## Upload an avatar

Upload a new avatar, and replace the current one if you have one.

### Request

```http request
POST /api/upload/avatar
Content-Type: multipart/form-data

file: <file>
```

### Example Response

Returns a 201 status on success, and the avatar URL in the response body.

```json
{
  "url": "https://cdn.miwa.lol/avatars/c950e071-75fd-4212-aab7-387fa5bda67b.png"
}
```

## Upload a background

Upload a new background, and replace the current one if you have one. It can be an image or a video.

:::note

Images will be converted to WebP format losslessly that can reduce the file size, which means faster loading times.

:::

### Request

```http request
POST /api/upload/background
Content-Type: multipart/form-data

file: <file>
```

### Example Response

Returns a 201 status on success, and the background URL in the response body.

```json
{
  "url": "https://cdn.miwa.lol/backgrounds/8162f53e-d186-41b2-a008-75551a9c1b0a.webp"
}
```

## Upload an audio

Upload a new audio. It will be added to your audio list.

### Request

:::note

The cover is optional, but it's recommended to provide one. It will be displayed in the audio player.

:::

```http request
POST /api/upload/audio
Content-Type: multipart/form-data

file: <file>
cover: <file> (optional)
name: <string>
```

### Example Response

Returns a 201 status on success, and the audio object in the response body.

```json
{
  "id": "2a7438fa-2821-47bb-8d00-ffa68628c7cd",
  "name": "A very cool music",
  "duration": 120, // In seconds
  "cover": "7c6d9e78-3ced-4f60-9357-19db54d19dfe" // "null" if you didn't provide a cover
}
```

:::tip

Covers URLs are just `https://cdn.miwa.lol/audios-covers/:id.png`, where `:id` is the cover ID (the one in the response).

:::

## Update an audio

Update an audio by its ID.

### Request

```http request
PATCH /api/upload/audio/:id
Content-Type: application/json
```

Example body:
```json
{
  // You can only update the name
  "name": "A very cool music"
}
```

### Example Response

Returns the updated audio object.

```json
{
  "id": "2a7438fa-2821-47bb-8d00-ffa68628c7cd",
  "name": "A very cool music",
  "duration": 120,
  "cover": "7c6d9e78-3ced-4f60-9357-19db54d19dfe"
}
```

## Delete an audio

Delete an audio by its ID.

### Request

```http request
DELETE /api/upload/audio/:id
```

### Example Response

Returns:
* a 204 status on success.
* a 404 status if the audio doesn't exist.
* a 403 status if the audio doesn't belong to you.

## Upload a custom cursor

Upload a new custom cursor, and replace the current one if you have one.

### Request

```http request
POST /api/upload/cursor
Content-Type: multipart/form-data

file: <file>
```

### Example Response

Returns a 201 status on success, and the cursor URL in the response body.

```json
{
  "url": "https://cdn.miwa.lol/cursors/de9bec09-f9d4-42c4-9e75-834bc5e3bdfb.cur"
}
```

## Upload a custom font

:::info

This endpoint is only available to Premium users.

:::

Upload a new custom font, and replace the current one if you have one.

### Request

```http request
POST /api/upload/font
Content-Type: multipart/form-data

file: <file>
```

### Example Response

Returns a 201 status on success, and the font URL in the response body.

```json
{
  "url": "https://cdn.miwa.lol/fonts/b3f66781-a5c8-4303-a6a3-807731b2ab93.ttf"
}
```