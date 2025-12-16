---
title: Triagio AI — Privacy Policy
permalink: /privacy-policy/
---

# Triagio AI — Privacy Policy

Last updated: 2025-12-16

This privacy policy explains what data Triagio AI (“we”, “us”) accesses, how it’s used, and the choices you have.

## What Triagio AI does

Triagio AI is a Chrome extension that:

- Connects to your Gmail account (with your permission).
- Reads incoming emails so it can turn them into tickets inside the extension.
- Can send emails on your behalf if you enable automatic replies.
- Can use AI to extract fields and generate summaries for tickets (optional, paid feature).

## Data we access

When you connect Gmail, the extension may access:

- Email metadata (sender, recipients, subject, timestamps, message IDs, thread IDs).
- Email content (snippets and message bodies) so tickets can be created.

If you enable automatic replies, the extension will send emails from your Gmail account using your connected account.

If you enable AI features, the extension sends the minimum needed to generate a result (typically client name, email subject, and email body) to our backend, which then calls an AI provider.

## Where data is stored

### In your browser (local)

Tickets, client mappings, and most settings are stored locally in your browser (Chrome extension storage / IndexedDB). This data stays on your device unless you remove the extension or clear browser data.

### On our backend (account + billing)

Our backend stores account and billing information needed to run the service, such as:

- Your account email address
- Subscription status and trial status
- Stripe customer/subscription identifiers

We do **not** store your Gmail messages as part of normal operation.

## Third parties we use

Triagio AI uses the following services to operate:

- **Google (Gmail API)**: to read emails and (if enabled) send replies.
- **Stripe**: to manage subscriptions and billing.
- **AI provider (OpenAI)**: to generate AI ticket extraction/summaries when you request AI features.

These providers process data according to their own privacy policies. We only share what’s necessary to provide the features you use.

## How we use your data

We use the data we access to:

- Create and display tickets in the extension.
- Keep a record of ticket activity (e.g. “ticket created”, “auto‑reply sent”).
- Send automatic replies if you enable that feature.
- Provide AI-assisted extraction/summaries if you request AI features.
- Operate billing and subscription management.

We do **not** sell your data and we do **not** use it for advertising.

## Your choices and controls

You can:

- Disconnect Gmail by removing the extension or revoking access in your Google Account.
- Disable automatic replies at any time in the extension Settings.
- Delete tickets inside the extension.
- Delete your account from inside the extension (this removes your backend account/billing record).

## Security

We use HTTPS for network communication. Access to protected backend routes requires authentication.

## Contact

If you have questions or want help, contact us at: **charles@acquah.io**
