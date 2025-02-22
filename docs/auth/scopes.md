---
title: OAuth2 Scopes
sidebar_position: 2
---

Scopes are used to grant access to specific resources and actions. They are used to limit the access of an access token to specific resources and actions. The scopes are defined by the API and are requested by the client during the authorization process.

## Available Scopes

The following scopes are available:

### `identify`

Grants access to the user's information, such as their username, display name, and avatar.

### `email`

Grants access to the user's email address.

### `profile.update`

Grants ability to update the user's profile, such as their username, display name, colors, effects, etc.

### `links`

Grants access to the user's links and the ability to create, update, and delete them.

### `cards`

Grants access to the user's cards and the ability to create and delete them.

### `audios.manage`

Grants ability to update and delete audios. For uploading audios, you need the `uploads` scope.

### `uploads`

Grants ability to upload an avatar, background, audios, custom cursor, and custom font uploads.

### `imagehost.upload`

Grants ability to upload images to the image host.

### `imagehost.delete`

Grants ability to delete images from the image host.