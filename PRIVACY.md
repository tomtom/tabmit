# Privacy Policy — TabMit

*Last updated: 2026-03-11*

## What TabMit does

TabMit is a browser extension that sends the content of the current browser tab to a destination of your choice: your default e-mail client, Gmail, or a Notion database. All transmissions are initiated explicitly by you — TabMit never acts automatically or in the background. TabMit does not collect any user data.

## What data is transmitted and where it goes

When you invoke a profile, TabMit reads the following data from the active tab and forwards it to the service you configured in that profile:

| Data | Destination |
|---|---|
| Page title | Your e-mail client, Gmail, or Notion |
| Page URL | Your e-mail client, Gmail, or Notion |
| Page content (HTML and/or plain text) | Your e-mail client, Gmail, or Notion |
| Images and stylesheets embedded in the page | Inlined into the email body (Gmail/clipboard profiles only); never sent to TabMit |

The destination is always a service that **you** control:

- **Default mail client (`mailto:`)** — data is passed to your operating system's default mail application via a `mailto:` URL. It never leaves your device until you click Send.
- **Gmail** — data is sent directly to `mail.google.com` to pre-fill a compose window or draft. TabMit does not use a server intermediary.
- **Notion** — data is sent to `api.notion.com` using the integration token you provided and stored. Pages are created in the Notion workspace and database you selected.

**No data is ever sent to the TabMit developer or any server operated by the developer.**

## What data is stored locally

TabMit stores the following data in your browser's `chrome.storage.sync` (or `browser.storage.sync` on Firefox), which is synced across your own devices by your browser sign-in:

| Item | Purpose |
|---|---|
| Profile definitions (name, client type, recipient address, body format, options) | Remembers your configured profiles |
| Notion integration token (`ntn_…`) | Authenticates requests to the Notion API |
| Default profile selection | Determines which profile is invoked by default |
| Recent submission log (URL + timestamp) | Powers the toolbar icon submission indicator |

This data is stored **only on your devices**. The developer has no access to it.

## Third-party services

When you use a Gmail or Notion profile, data is transmitted to those services. Their own privacy policies apply:

- Gmail / Google: https://policies.google.com/privacy
- Notion: https://www.notion.so/privacy

## Permissions used

| Permission | Why it is needed |
|---|---|
| `activeTab` | Read the current tab's title, URL, and content when you click the toolbar button |
| `scripting` | Inject a one-shot script to capture the live page DOM (title, URL, HTML, selected text) |
| `storage` | Persist your profiles and settings in `chrome.storage.sync` |
| `contextMenus` | Add profiles to the browser right-click menu |
| `clipboardWrite` | Write self-contained HTML to the clipboard for clipboard-mode profiles |
| `notifications` | Show a brief confirmation notice after a page is submitted |
| `bookmarks` | Read bookmarks from a user-selected folder to submit multiple pages in sequence (bookmark-folder profiles) |
| `offscreen` | Run a hidden document with DOM access so the service worker can parse and inline HTML (Chrome only) |
| `identity` | Obtain a Google OAuth token to authenticate Gmail API calls (Chrome only; disabled in current release) |
| `host_permissions: <all_urls>` | Fetch images and stylesheets from any domain for inlining into Gmail/clipboard email bodies |
| `host_permissions: gmail.googleapis.com` | Send Gmail API requests (draft creation) on behalf of the authenticated user |
| `host_permissions: api.notion.com` | Send page content to the Notion API using the integration token you provided |

## Contact

Questions or concerns: [github.com/tomtom/tabmit/issues](https://github.com/tomtom/tabmit/issues)
