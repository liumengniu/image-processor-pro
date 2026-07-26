# Privacy Policy

## WhatsApp Group Invite Code Privacy Policy

### Last Updated: July 26, 2026

Thank you for using the **WhatsApp Group Invite Code** Chrome extension. This privacy policy explains how the extension handles your information.

**TL;DR — we collect nothing. All data stays on your device.**

---

## Information Collection and Use

### What We Do NOT Collect

This extension **does NOT collect, store, transmit, or upload** any personal information or user data, including but not limited to:

- Your WhatsApp account information (phone number, profile name, avatar, etc.)
- Your contact list
- Your chat history or message content
- Group metadata (member lists, group IDs, group descriptions, etc.)
- The invite codes you fetch
- Browsing history outside of `web.whatsapp.com`
- Device information, IP address, or any identifying data
- Cookies, session tokens, or authentication data

### What Stays on Your Device

The extension reads the following data **only at the moment you click the "Get Invite Link" button**, entirely inside your browser, and uses it only to display the result in the popup:

1. The **group ID** of the chat currently active in WhatsApp Web (read from WhatsApp Web's in-page JavaScript module `WAWebChatCollection`)
2. The **invite code** returned by WhatsApp Web's in-page module `WAWebMexFetchGroupInviteCodeJob` — this is the same code that WhatsApp itself generates when you click "Invite to group via link" inside WhatsApp Web

Both values are immediately shown in the extension popup. They are never written to disk, never sent off your device, and are discarded as soon as the popup is closed.

### Local Processing Only

All features are executed locally in your browser:

1. **Get Invite Link** — Invokes WhatsApp Web's own in-page function via a content script and displays the result in the popup
2. **Copy Link** — Copies the invite link to your clipboard using the browser's standard Clipboard API
3. **Status Messages** — Error/success messages are displayed in the popup only; nothing is logged or uploaded

There is no background sync, no remote server, no telemetry, and no analytics.

---

## Data Flow

```
You click "Get Invite Link" in the popup
        ↓
Background service worker injects a small script into the WhatsApp Web page
        ↓
Script calls WhatsApp Web's own in-page module to fetch the invite code
        ↓
Invite code is shown in the popup and (optionally) copied to your clipboard
        ↓
Nothing is sent anywhere
```

At no point does the extension send data to any server we control, any third-party server, or any analytics service.

---

## Permission Usage

This extension requests the following permissions:

| Permission | Purpose | Description |
|------------|---------|-------------|
| `activeTab` | Access the current tab | Only activates when you click the extension icon; used to identify the WhatsApp Web tab |
| `scripting` | Inject script into the page | Required to call WhatsApp Web's internal JavaScript modules via `chrome.scripting.executeScript({ world: "MAIN" })` |
| `tabs` | Create / focus tabs | When you are not on WhatsApp Web, clicking the button opens `web.whatsapp.com` in a new tab so you can use the extension |
| `host_permissions: web.whatsapp.com` | Host permission | Restricts the extension to running only on `https://web.whatsapp.com/*`; no other site is touched |

**We will NOT**:

- Access any website other than `web.whatsapp.com`
- Read or modify webpage content on any other site
- Monitor your browsing history
- Access other extensions or your system
- Install any additional software
- Upload any data to any server (ours, third-party, or otherwise)
- Track you across sites or sessions

---

## Third-Party Services

This extension:

- Does not use any third-party analytics services (no Google Analytics, no Sentry, no Mixpanel, etc.)
- Does not contain any advertising, ad networks, or affiliate trackers
- Does not include any social-media pixels or fingerprinting libraries
- Does not communicate with any external server (the only network traffic is the WhatsApp Web page itself, which is initiated by your browser, not by the extension)

### Embedded QR Code in the Popup

The popup displays a static QR code image (`icons/whatsapp-qr.png`) bundled inside the extension package. This image is the developer's personal WhatsApp contact, included so users can reach the developer if they have a problem. The QR code:

- Is embedded in the extension ZIP and is identical for every user
- Does not identify you or your device in any way
- Is not generated from, and does not reference, your WhatsApp account
- Can be ignored entirely; using the extension does not require scanning it

---

## Data Security

Because we do not collect, store, or transmit any data, there is no risk of data leakage or misuse from our side. The only data that ever exists outside of WhatsApp Web's own session is the invite code that is briefly displayed in your popup before you copy it. You remain in full control of that string.

---

## Children's Privacy

This extension does not target children under 13 and does not knowingly collect any information from anyone, including children. Since no data is collected at all, this policy applies uniformly to all users.

---

## Changes to WhatsApp Web

This extension relies on the internal JavaScript modules `WAWebChatCollection` and `WAWebMexFetchGroupInviteCodeJob` that WhatsApp Web exposes inside its own page context. WhatsApp may rename, refactor, or remove these modules at any time. If that happens:

- The extension will display a clear error message in the popup (e.g. "Extension is not ready, please refresh WhatsApp Web")
- No data is collected as a side effect
- No update to this privacy policy is required

---

## Privacy Policy Updates

If we make any material change to this privacy policy, we will:

1. Update the "Last Updated" date at the top of this file
2. Note the change in the extension's update log / `submit.md` changelog
3. Republish the extension to the Chrome Web Store

Continued use of the extension after an update constitutes acceptance of the revised policy.

---

## Open Source

This extension is open source. You can inspect the complete source code in the public repository to verify these claims yourself. The injected script (`content/inject.js`) is short (~80 lines) and only contains the WhatsApp module calls described above.

---

## Contact Us

If you have any questions or suggestions about this privacy policy, or if you want to report a privacy concern, please reach us through:

- The developer's WhatsApp (QR code inside the extension popup)
- The Chrome Web Store support / report abuse form
- The issue tracker on the public source repository

---

## Disclaimer

**Note**: This extension is an unofficial, third-party helper tool. It is not affiliated with, endorsed by, or sponsored by WhatsApp LLC or Meta Platforms, Inc. "WhatsApp" is a trademark of WhatsApp LLC. Please comply with WhatsApp's Terms of Service and applicable laws when using this extension. The developers are not responsible for misuse of the generated invite links.