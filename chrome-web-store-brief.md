# Triagio AI — Chrome Web Store submission brief (for Atlas)

## Product

- **Name:** Triagio AI
- **Short description:** Turn client emails into tickets. Triage and reply without leaving your inbox.
- **Current build:** `triagio-ai-0.1.4.zip` (see `client-tickets/extension/triagio-ai-0.1.4.zip`)
- **Unpacked build:** `client-tickets/extension/dist`

## What it does (user-facing)

- Connects a Gmail account and watches for incoming emails.
- Turns emails into tickets in an internal board (Not started / In progress / Finished).
- Supports client directories (map email → client).
- Ticket detail view includes:
  - User email text (rendered and clearly marked)
  - Optional AI summary generation
  - Activity log (including auto-reply status)
- Refresh button pulls latest emails and shows visible “refreshing” feedback.
- Settings include automatic replies (optional), watched mailbox status, and backend URL (advanced).
- Subscription billing via Stripe:
  - Subscribe / manage billing / cancel
  - Trial support

## Backend

- **Base URL (production):** `https://client-tickets-backend-fcab68d0061d.herokuapp.com`
- Health endpoint: `GET /health`
- Billing:
  - `POST /billing/create-checkout-session`
  - `POST /billing/create-portal-session`
  - `POST /billing/cancel-subscription`
  - `POST /billing/sync`
  - Billing landing pages for Stripe redirects:
    - `GET /billing/success`
    - `GET /billing/cancel`
    - `GET /billing/portal-return`
- AI (protected): `POST /ai/extract` (requires auth + active trial/subscription)

## Permissions + justifications (manifest v3)

### Chrome permissions

- `storage` — store local tickets, client directory mappings, and settings.
- `identity` — sign in / connect Gmail via Google OAuth.
- `notifications` — notify the user about important events (errors, refresh outcomes) when needed.
- `alarms` — schedule background refresh / email polling tasks.

### Host permissions

- `https://gmail.googleapis.com/*` — read Gmail messages and send replies (if enabled).
- `https://www.googleapis.com/oauth2/*` — get Google user info during sign-in.
- `https://client-tickets-backend-fcab68d0061d.herokuapp.com/*` — auth, billing, and AI extraction endpoints.

## Data disclosure notes (for Chrome Web Store “Data safety”)

Triagio AI accesses **personal communications** (Gmail messages) to create tickets and optionally send auto-replies.

Data handling (high level):

- Tickets and settings are stored **locally in the browser** (Chrome extension storage / IndexedDB).
- The backend stores **account + billing** identifiers (email, subscription status, Stripe IDs).
- For AI features, the extension sends **client name + email subject/body** to the backend, which sends it to an AI provider to generate a structured extraction / summary.
- Users can delete their account from inside the extension.

## Links required in listing

- **Privacy policy URL:** publish via GitHub Pages (see `client-tickets/docs/privacy-policy.md`) and paste the resulting URL here.
- **Support email:** charles@acquah.io
- **Support site / contact page (optional):** https://acquah.io

## Notes for review

- The extension requires Gmail scopes (`gmail.readonly`, `gmail.send`). Customers must grant access to connect Gmail.
- If the Chrome Web Store extension ID changes, update:
  - Heroku `CORS_ORIGIN=chrome-extension://<EXT_ID>`
  - Google OAuth redirect URI: `https://<EXT_ID>.chromiumapp.org/`
