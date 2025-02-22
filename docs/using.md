---
title: Using the API
sidebar_position: 2
---

Our API uses OAuth2 for authentication and authorization. This means that you need to obtain an access token to access the API. The access token is used to authenticate your requests to the API and to limit the access of the token to specific resources and actions. See the [OAuth2](/oauth2) documentation for more information on how to obtain an access token.

## Base URL

The base URL for the API is `https://miwa.lol/api`. All API requests should be made to this URL.

## Authentication

To authenticate your requests to the API, you need to include the access token in the `Authorization` header of your requests. The access token should be prefixed with `Bearer` and followed by a space. For example:

```
Authorization: Bearer <access_token>
```
