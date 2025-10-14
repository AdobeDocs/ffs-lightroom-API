---
title: Lightroom API Authentication
description:  Lightroom authentication and instructions for using server-to-server authentication credentials to let your application's server generate access tokens.
hideBreadcrumbNav: true
keywords:
- authentication
- OAuth
- server-to-server
- access token
- Lightroom API
- Adobe API
- client credentials
- API security
- developer console
- enterprise authentication
- Firefly Services
contributors:
  - https://github.com/BaskarMitrah
  - https://github.com/aeabreu-hub
---

# Authentication

Use server-to-server authentication credentials that allow your application's server to generate access tokens and make API calls.

## Overview

For your application to generate an access token, an end user doesn't need to sign in or provide consent to your application. Instead, your application can use its credentials (Client ID and Secret) to authenticate itself and generate access tokens. Your application can then use these to call Adobe APIs and services on its behalf.

This is sometimes referred to as "two-legged OAuth".

Automate your token generation by calling the endpoint using standard OAuth2 libraries. Using industry-standard libraries is the quickest and most secure way of integrating with OAuth. Be diligent when choosing the OAuth 2.0 library that works best for your application. Your teams' projects likely leverage OAuth libraries already to connect with other APIs. It's recommended to use these libraries to automatically generate tokens when they expire.

## Prerequisites

Work with your Adobe representative to get the following:

- An [Adobe Developer Console][1] account.
- An active Enterprise contract with Firefly Services included.
- A [project][2] with Lightroom API [OAuth Server-to-Server credentials set up][3].
- Access to your **Client ID** and **Client Secret** from the [Adobe Developer Console project][4]. Securely store these credentials and never expose them in client-side or public code.

## Retrieve an access token

A temporary access token validates calls to the API. [This token can be generated directly in the Developer Console][5],
or by following the steps below.

1. First, open a secure terminal and export your **Client ID** and **Client Secret** as environment variables so that later commands can access them:

```bash
export LR_FF_SERVICES_CLIENT_ID=<Your_Client_ID>
export LR_FF_SERVICES_CLIENT_SECRET=<Your_Client_Secret>
```

2. Generate access tokens programmatically by sending a POST request:

```bash
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
-H 'Content-Type: application/x-www-form-urlencoded' \
-d 'grant_type=client_credentials' \
-d "client_id=$LR_FF_SERVICES_CLIENT_ID" \
-d "client_secret=$LR_FF_SERVICES_CLIENT_SECRET" \
-d 'scope=openid,AdobeID,read_organizations'
```

The required parameters are:

- `client_id`: The Client ID.
- `client_secret`: The Client secret.
- `scope`: The scopes are `openid`, `AdobeID`, `read_organizations`.

The response will look like the example below:

```json
{
    "access_token": "exampleAccessTokenAsdf123",
    "token_type": "bearer",
    "expires_in": 86399
}
```

Each access token is valid for 24 hours. To adhere to OAuth best practices, generate a new token every 23 hours.

3. Export your access token as an environment variable:

```bash
export LR_FF_SERVICES_ACCESS_TOKEN=<Your_Access_Token>
```

<!-- Links -->
[1]: https://developer.adobe.com/
[2]: https://developer.adobe.com/developer-console/docs/guides/projects/projects-empty/
[3]: https://developer.adobe.com/developer-console/docs/guides/services/services-add-api-oauth-s2s/
[4]: https://developer.adobe.com/developer-console/docs/guides/services/services-add-api-oauth-s2s/#api-overview
[5]: https://developer.adobe.com/developer-console/docs/guides/services/services-add-api-oauth-s2s#generate-token
