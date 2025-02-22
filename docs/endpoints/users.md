---
title: Users
sidebar_position: 1
---

This page contains information about the `/users` endpoint.

## Get a user

Get a user by their username.

### Request

`:username` is the username of the user you want to get. It can be a username or an alias.

```http request
GET /api/user/:username
```

### Example Response

```json
{
  "id": "28b841e9-1d54-4142-9b15-5050d620c0ea",
  "username": "yuuto",
  "display_name": "Yuuto",
  "alias": "$",
  "bio": "🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸",
  "discord_id": "269415459735076864",
  "created_at": 1000,
  "is_premium": true,
  "volume_control": true,
  "page_enter_text": null,
  "layout": "modern",
  "assets": {
    "avatar": "https://cdn.miwa.lol/avatars/40380b72-5045-45b2-aa5f-9b806209e762.jpg",
    "cursor": null,
    "background": "https://cdn.miwa.lol/backgrounds/e893dbf5-3e6b-4246-9118-e33afa17948c.webp",
    "audios": [
      "https://cdn.miwa.lol/audios/a12593fe-b6dd-4731-ae38-1ebf304a00db.mp3",
      "https://cdn.miwa.lol/audios/084214bd-c213-4578-857e-ad935fb924cc.mp3",
      "https://cdn.miwa.lol/audios/cdc68c1d-34e2-4d0a-a842-59e02a20dbbc.mp3"
    ],
    "use_discord_avatar": false,
    "shuffle_audios": true,
    "play_all_audios": true
  },
  "profile": {
    "opacity": 20,
    "blur": 9,
    "font": "Fira Mono"
  },
  "colors": {
    "accent": "#bd10e0",
    "text": "#ffffff",
    "background": "#000000",
    "badge": "#fff",
    "link": "#ffffff",
    "monochrome_links": true
  },
  "effects": {
    "background": "snowflakes",
    "cursor": "fairy-dust",
    "username": "rainbow"
  },
  "tab": {
    "animated_title": "reverse",
    "use_avatar": true
  },
  "privacy": {
    "hide_views": false,
    "hide_badges": false,
    "hide_join_date": false,
    "hide_likes": false,
    "search_engines_indexing": true
  },
  "typewriter": {
    "enabled": true,
    "texts": [
      "dev & owner @ miwa.lol",
      "discord.gg/miwa"
    ]
  }
}
```

## Get your user

Get the user that is currently authenticated.

### Request

```http request
GET /api/user
```

### Example Response

This is practically the same as the response from the previous endpoint, but with some differences.

```json
{
  "id": "28b841e9-1d54-4142-9b15-5050d620c0ea",
  "username": "yuuto",
  "display_name": "Yuuto",
  "alias": "$",
  "email": "your@email.com",
  "custom_domain": null,
  "bio": "🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸🇬🇸",
  "discord_id": "269415459735076864",
  "created_at": 1000,
  "is_premium": true,
  "otp_enabled": true,
  "volume_control": true,
  "page_enter_text": "hi click pls",
  "locale": "fr",
  "layout": "modern",
  "assets": {
    "avatar": "https://cdn.miwa.lol/avatars/40380b72-5045-45b2-aa5f-9b806209e762.jpg",
    "cursor": null,
    "background": "https://cdn.miwa.lol/backgrounds/e893dbf5-3e6b-4246-9118-e33afa17948c.webp",
    "audios": [
      "https://cdn.miwa.lol/audios/a12593fe-b6dd-4731-ae38-1ebf304a00db.mp3",
      "https://cdn.miwa.lol/audios/084214bd-c213-4578-857e-ad935fb924cc.mp3",
      "https://cdn.miwa.lol/audios/cdc68c1d-34e2-4d0a-a842-59e02a20dbbc.mp3"
    ],
    "use_discord_avatar": false,
    "shuffle_audios": true,
    "play_all_audios": true
  },
  "profile": {
    "opacity": 20,
    "blur": 9,
    "font": "Fira Mono"
  },
  "colors": {
    "accent": "#bd10e0",
    "text": "#ffffff",
    "background": "#000000",
    "badge": "#fff",
    "link": "#ffffff",
    "monochrome_links": true
  },
  "effects": {
    "background": "snowflakes",
    "cursor": "fairy-dust",
    "username": "rainbow"
  },
  "tab": {
    "animated_title": "reverse",
    "use_avatar": true
  },
  "privacy": {
    "hide_views": false,
    "hide_badges": false,
    "hide_join_date": false,
    "search_engines_indexing": true
  },
  "typewriter": {
    "enabled": true,
    "texts": [
      "dev & owner @ miwa.lol",
      "discord.gg/miwa"
    ]
  }
}
```

## Update your profile

Allows you to update your profile, including your username, display name, alias, bio, and more.

### Request

```http request
PATCH /api/user
```

### Example Request

For example, to update your accent color:

```json
{
  "colors": {
    "accent": "#bd10e0"
  }
}
```

### Response

Returns the updated user object.