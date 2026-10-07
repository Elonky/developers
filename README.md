# Elonky Developers

Official community and support hub for developers building integrations with the [Elonky](https://elonky.com) marketplace platform.

[Documentation](https://developer.elonky.com/en/documentation/) · [API Reference](https://developer.elonky.com/en/reference/) · [Discussions](https://github.com/Elonky/developers/discussions) · [Issues](https://github.com/Elonky/developers/issues)

## What is this repository?

This is the place to ask questions, report problems and share feedback about the Elonky Integration APIs. It is a community and support space only. It does not contain Elonky's source code.

Everything you need to build an integration lives on [developer.elonky.com](https://developer.elonky.com). Use this repository when the documentation is not enough.

## API status

Elonky Open API **v1** currently includes the following Integration APIs:

| API | Purpose |
|---|---|
| **Auth API** | Exchange integration credentials for a short-lived access token |
| **Product API** | Product listing, inventory updates and product details |
| **Store API** | Store information for the authenticated integration |
| **Order API** | Order retrieval and fulfillment status updates |
| **Category API** | Read-only product category mapping |

Other domains stay marked as "coming soon" in the [API Reference](https://developer.elonky.com/en/reference/) until their public routes and specifications are verified. Every change is announced in [Announcements](https://github.com/Elonky/developers/discussions/categories/announcements).

## Getting started

1. **Create credentials.** Sign in to the Elonky Shop Dashboard, open **Shop Settings → Developer**, enter an integration name, select the minimum scopes you need and create the integration.
2. **Store the secret safely.** The client secret is shown only once. Copy the client ID and client secret into a server-side secret manager.
3. **Request an access token** from your backend:

   ```bash
   curl --request POST 'https://auth.elonky.com/api/developer/v1/oauth/token' \
     --header 'Content-Type: application/json' \
     --data '{
       "clientId": "<clientId>",
       "clientSecret": "<clientSecret>"
     }'
   ```

   The response contains a Bearer access token that expires after 60 minutes.

4. **Make your first authenticated request:**

   ```bash
   curl --request GET 'https://edge.elonky.com/api/store/v1/integration/stores/info' \
     --header 'Accept: application/json' \
     --header 'Authorization: Bearer <accessToken>'
   ```

Never expose the client secret or access token in browser code. A shop can have up to five integrations, so use a separate one for each external system. Read the full [Integration Guide](https://developer.elonky.com/en/documentation/) for details.

## Where should I post?

| I want to... | Go to |
|---|---|
| Create credentials, choose scopes, request tokens or fix 400/401 errors | [Authentication & Credentials](https://github.com/Elonky/developers/discussions/categories/authentication-credentials) |
| Work with products, categories, shipping and return profiles, media or inventory | [Products & Catalog](https://github.com/Elonky/developers/discussions/categories/products-catalog) |
| List orders, update order status or work with carriers | [Orders & Fulfillment](https://github.com/Elonky/developers/discussions/categories/orders-fulfillment) |
| Ask about the Store API or anything else | [Q&A](https://github.com/Elonky/developers/discussions/categories/q-a) |
| Check known problems and incidents | [Known Issues & Status](https://github.com/Elonky/developers/discussions/categories/known-issues-status) |
| Suggest a new endpoint, field or improvement | [Ideas](https://github.com/Elonky/developers/discussions/categories/ideas) |
| Share your integration, SDK or tool | [Show and tell](https://github.com/Elonky/developers/discussions/categories/show-and-tell) |
| Report a reproducible API bug or a documentation error | [Open an issue](https://github.com/Elonky/developers/issues/new/choose) |
| Get help with something account-specific or private | [support@elonky.com](mailto:support@elonky.com) or [elonky.com/en/contact](https://elonky.com/en/contact) |
| Report a security vulnerability | [Private security advisory](https://github.com/Elonky/developers/security/advisories/new) |

## How to ask a good question

Please include:

- The API and endpoint you are calling, for example `POST /api/product/v1/integration/products`
- The timestamp and the HTTP status code you received
- A trace or correlation ID, if one was returned
- A sanitized request and response
- What you expected to happen and what happened instead

## Keep secrets out of public posts

**Never post** client IDs, client secrets, access tokens, passwords or customer personal data (names, addresses, emails, order details) in Discussions or Issues. Replace sensitive values with `<redacted>` before sharing curl, Postman or log output.

If you accidentally post a credential, edit or delete the post and **rotate the secret immediately** in Shop Dashboard → Shop Settings → Developer. Rotating prevents the old secret from issuing new tokens. Elonky may remove posts that expose credentials or personal data to protect you.

To report a security vulnerability, use a [private security advisory](https://github.com/Elonky/developers/security/advisories/new) and never open a public issue. See our [security policy](SECURITY.md).

## What to expect

Community support in this repository is provided on a best-effort basis by the Elonky team and other developers. Official updates, breaking changes and deprecations are always published in [Announcements](https://github.com/Elonky/developers/discussions/categories/announcements). For urgent or account-specific problems, contact [support@elonky.com](mailto:support@elonky.com).

## Languages

The documentation is available in English, Türkçe and 日本語. Discussions are in English, but questions in Turkish and Japanese are welcome.

## Feedback

We welcome feature requests, endpoint and schema suggestions, bug reports and documentation fixes. By submitting feedback you grant Elonky a non-exclusive, worldwide, royalty-free license to use it to improve our APIs, documentation and services.

## Community guidelines

Everyone taking part in this repository is expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md). Please be respectful, constructive and welcoming.

---

© 2026 Elonky, Inc. All rights reserved. Use of the Elonky APIs is subject to the [Terms of Use](https://elonky.com/en/contract/terms-of-use) and [Privacy Policy](https://elonky.com/en/contract/privacy-policy).
