---
title: OAuth2
sidebar_position: 1
sidebar_label: OAuth2
description: Learn how to authenticate with the API using OAuth2.
---

OAuth2 clients are used to authenticate with the API. They are used to generate access tokens which are used to authenticate requests to the API.

:::info

If you are looking for a way to authenticate with the API without user interaction, see [Client Credentials](/auth/client-credentials).

:::

## Creating an OAuth2 client

To create an OAuth2 client, please access the [developers settings](https://miwa.lol/dashboard/settings/developers), and click on the "Create a new client" button.

You will be prompted to enter the following information:
- **Name**: The name of your app
- **Description**: A description of your app
- **Redirect URI**: The URI where users will be redirected after authorizing the app
- **Terms of Service URL**: A URL to your app's terms of service, if applicable
- **Privacy Policy URL**: A URL to your app's privacy policy, if applicable

After entering the information, click on the "Create" button. You will be provided a Client ID and Client Secret. Keep these safe, as they are used to authenticate with the API.

:::danger

The client secret should **never** be exposed on the client-side. It should only be used server-side.

:::

## Authorizing an OAuth2 client

To authorize an OAuth2 client, you must visit the following URL:

```
https://miwa.lol/oauth2/authorize?client_id=<YOUR_CLIENT_ID>&redirect_uri=<YOUR_REDIRECT_URI>&response_type=code&scope=<SCOPES>
```

Replace:
- `<YOUR_CLIENT_ID>` with your OAuth2 app's client
- `<YOUR_REDIRECT_URI>` with your OAuth2 app's redirect URI
- `<SCOPES>` with the scopes you want to request, separated by a space. See [Scopes](/auth/scopes.md) for more information.

After visiting the URL, you will be prompted to log in and authorize the app. If you authorize the app, you will be redirected to the redirect URI with a `code` query parameter.
See the next section for information on exchanging the authorization code for an access token.

## Exchanging the Authorization Code for an Access Token

To exchange the authorization code for an access token, you must make a `POST` request to the following URL: `https://miwa.lol/api/oauth2/token`.

The request must include the following parameters:

- `client_id`: Your OAuth2 app's client ID
- `client_secret`: Your OAuth2 app's client secret
- `code`: The authorization code you received
- `grant_type`: `authorization_code`
- `redirect_uri`: Your OAuth2 app's redirect URI

If the request is successful, you will receive a JSON response with an `access_token` and `refresh_token`.

:::info

Access tokens expires after one hour. You can refresh the access token using the refresh token (see [Refreshing an Access Token](#refreshing-an-access-token)), which expires after 7 days.

:::

:::danger

The `client_secret` should **never** be exposed on the client-side. It should only be used server-side.

:::

### Example

Here is an example of how to exchange an authorization code for an access token using `curl`:

```bash
curl -X POST https://miwa.lol/api/oauth2/token \
    -H "Content-Type: application/x-www-form-urlencoded" \
    -d "client_id=YOUR_CLIENT_ID" \
    -d "client_secret=YOUR_CLIENT_SECRET" \
    -d "code=157845" \
    -d "grant_type=authorization_code" \
    -d "redirect_uri=https://example.com/callback"
```

## Refreshing an Access Token

Access tokens expire after a certain amount of time. To refresh an access token, you must make a `POST` request to the following URL: `https://miwa.lol/api/oauth2/token`.

The request must include the following parameters:
- `client_id`: Your OAuth2 app's client ID
- `client_secret`: Your OAuth2 app's client secret
- `refresh_token`: The refresh token you received
- `grant_type`: `refresh_token`

If the request is successful, you will receive a JSON response with a new `access_token` and `refresh_token`.

### Example

Here is an example of how to refresh an access token using `curl`:

```bash
curl -X POST https://miwa.lol/api/oauth2/token \
    -H "Content-Type: application/x-www-form-urlencoded" \
    -d "client_id=YOUR_CLIENT_ID" \
    -d "client_secret=YOUR_CLIENT_SECRET" \
    -d "refresh_token=YOUR_REFRESH_TOKEN" \
    -d "grant_type=refresh_token"
```

## Revoking an Access Token

:::warning

You can't revoke access tokens at the moment. This will be added in the future.

:::