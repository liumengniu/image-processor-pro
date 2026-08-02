# Privacy Policy — Instagram DM™ Real-time Translation

**Last updated:** 2026-07-30

## Overview

Instagram DM™ Real-time Translation ("the Extension") is a browser extension that translates
messages on Instagram DM Web A (`https://www.instagram.com/*`) using the public
translation backend `https://tranai.app/api`.

This policy describes what data the Extension collects, how it is used, and
how it is stored.

## Data Collection

### 1. Account & Authentication

The Extension requires you to log in to a `tranai.app` account to use the
translation service. The following data is collected at login:

- Username / password (sent only to `tranai.app/api`, **never** stored locally)
- Token returned from `tranai.app/api/login` (stored locally in
  `chrome.storage.local` as `instagram_dm_token`)
- Customer / account info returned by the backend (stored as `instagram_dm_customer`)
- Device ID (random UUID generated locally, stored as `instagram_dm_device_id`)
- Token expiration timestamp (stored as `instagram_dm_expiration_time`)

### 2. Message Translation

When you trigger a translation (manually or via auto-translate):

- The **source text** of the selected message is sent to
  `https://api.tranai.app/api/translate/trans` or
  `https://tranai.app/api/translator/common`
- The **translated text** is returned by the backend and rendered locally
- Translation **cache** entries are stored in IndexedDB under the database
  name `instagram_cache_db`, table `translations`
- Cache key = hash of (source text + source language + target language +
  channel + scene + tone)
- Cached entries may be cleared by the user via the Extension's settings
  (see "User Controls" below)

The Extension **does not** send to the backend:

- Surrounding DOM (only the message text is sent)
- User identity on Instagram DM (your TG account ID, username, phone number)
- Conversation metadata (chat names, member lists)
- Any other data on the page

### 3. Settings

The Extension stores the following settings in `chrome.storage.local` under the
key `instagram_dm_settings`:

- Target language, channel, scene, tone
- Auto-translate toggle
- Translation blacklist (chat names / languages to skip)
- Font color, display preferences

Settings are **synced only to your local Chrome profile**, never transmitted
to the backend.

### 4. Anonymous Telemetry (Optional — Future)

The current version **does not** collect telemetry. If telemetry is added in a
future version, it will be opt-in and disclosed in an updated version of this
policy.

## Data Storage

| Data | Location | Encrypted? | Lifetime |
|---|---|---|---|
| Login token | `chrome.storage.local` | No (Chrome-managed) | Until logout or expiration |
| Customer info | `chrome.storage.local` | No | Until logout |
| Settings | `chrome.storage.local` | No | Until cleared by user |
| Translation cache | IndexedDB (`instagram_cache_db`) | No | Until cleared by user |

Translation cache is stored locally and never leaves your device. No remote
persistence of cache is performed.

## Third-Party Services

The Extension integrates with:

| Service | URL | Purpose |
|---|---|---|
| `tranai.app` | `https://tranai.app/api` | Authentication & dictionary lookup |
| `api.tranai.app` | `https://api.tranai.app/api/translate/trans` | Translation |
| `www.instagram.com` | `https://www.instagram.com/a` | Host page (read-only access) |

The Extension does **not** modify any data on `www.instagram.com`. It only
renders translated text in a layer over the existing UI.

## User Controls

You can control the Extension's data collection at any time:

- **Log out** — clears token, customer info, device ID, expiration time
  (in popup or settings page)
- **Clear translation cache** — clears all entries in `instagram_cache_db`
- **Disable auto-translate** — translation only triggered on manual action
- **Uninstall the Extension** — automatically clears all `chrome.storage.local`
  entries and the IndexedDB database

## Children

The Extension is not intended for users under 13. We do not knowingly collect
data from children.

## Changes to This Policy

We may update this policy to reflect changes in the Extension or in applicable
laws. The "Last updated" date at the top of this document will reflect the
most recent change. Material changes will be communicated through the Extension's
Chrome Web Store listing.

## Contact

For privacy inquiries, please contact:

`privacy@instagram-dm-translator.example`

(Replace with actual contact before publishing.)

## Disclaimer

This Extension is an independent project. It is **not affiliated with,
endorsed by, or sponsored by Instagram DM FZ-LLC or WhatsApp LLC.** Instagram DM is a
trademark of Instagram DM FZ-LLC. WhatsApp is a trademark of WhatsApp LLC.
