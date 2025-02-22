---
title: Client Credentials
sidebar_position: 3
---

Client credentials are used to authenticate with the API. They are another way to generate access tokens which are used to authenticate requests to the API.

An advantage of client credentials is that **they do not require user interaction** (like OAuth2, which requires the user to authorize the app). This makes them ideal for server-to-server communication.

:::warning

As client credentials do not require user interaction, the authenticated user will always be the one who created the OAuth2 client. Since there is no user approval step (e.g., "Do you authorize this app to access your account?"), no scopes are needed. This means the client automatically has access to all available endpoints.

:::

## Using Client Credentials

:::note

You first need to create an OAuth2 client. See [Creating an OAuth2 Client](/auth/oauth2#creating-an-oauth2-app) for more information.

:::

After creating a client, you will receive a `client_id` and a `client_secret`. These are the credentials you will use to authenticate with the API, by creating an access token:

```bash
curl -X POST https://miwa.lol/api/oauth2/token \
    -H "Content-Type: application/x-www-form-urlencoded" \
    -d "grant_type=client_credentials" \
    -d "client_id=YOUR_CLIENT_ID" \
    -d "client_secret=YOUR_CLIENT_SECRET"
```

Replace `YOUR_CLIENT_ID` and `YOUR_CLIENT_SECRET` with your OAuth2 client's `client_id` and `client_secret`.

If the request is successful, you will receive a JSON response with an `access_token` and `expires_in`. For example:

```json
{
  "access_token": "your_access_token",
  "token_type": "bearer",
  "expires_in": 3600
}
```

:::info

Access tokens expire after one hour. Once expired, you will need to request a new access token using the same client credentials.

:::

## Using the Access Token

To authenticate requests to the API, you must include the access token in the `Authorization` header:

```bash
Authorization: Bearer <access_token>
```

Replace `<access_token>` with the access token you received.