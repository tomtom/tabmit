# TabMit

**Submit the current tab by e-mail.**

TabMit adds a toolbar button to your browser. One click sends the current page — title, URL, and content — to your mail client, Gmail, or Notion. You can define as many named profiles as you like (different recipients, clients, or formats).

Bug reports and feature requests: [github.com/tomtom/tabmit/issues](https://github.com/tomtom/tabmit/issues)

---

## Install on Chrome

1. Open the [Chrome Web Store listing](#) *(link to be added after publication)* and click **Add to Chrome**.
2. The TabMit icon appears in the toolbar. If it is hidden behind the puzzle-piece menu, click the puzzle piece and pin **TabMit**.

**Developer / unpacked install:**

1. Go to `chrome://extensions` and enable **Developer mode**.
2. Click **Load unpacked** and select the project folder (the one containing `manifest.json`).

---

## Install on Firefox

### Desktop (Firefox 140+)

Install from [Firefox Add-ons (AMO)](https://addons.mozilla.org/en-US/firefox/addon/tabmit/)

**Temporary install (development):**

1. Open `about:debugging` → **This Firefox** → **Load Temporary Add-on…**
2. Select `manifest.json` from the extracted `tabmit-firefox.zip`.

The extension stays active until Firefox restarts.

### Firefox for Android (Firefox 142+)

The simplest method is via Firefox Account sync:

1. Install TabMit permanently on Firefox Desktop (from AMO).
2. Sign in to your Firefox Account on both desktop and Android.
3. The extension syncs automatically to Android.

---

## Quick Start: Configure Profiles

1. **Open Settings** — right-click the TabMit toolbar icon → **Settings…**
   *(Firefox: left-click the icon → ⚙ Settings)*
2. Click **+ Add profile**.
3. Fill in:
   - **Name** — shown in the click menu (e.g. "Work Outlook").
   - **Client** — choose from the table below.
   - **Recipient** — default `To:` address (may be left blank).
4. Click **Save**.

---

## Client Types

| Client | What it does | Setup required |
|---|---|---|
| **Default mail client** (`mailto:`) | Opens Windows Mail, Outlook, Thunderbird, etc. with the page title as subject and plain text as body (truncated to ~1 800 chars) | None |
| **Gmail – plain text** | Opens a Gmail compose tab with the page title as subject and plain text as body | None |
| **Gmail – clipboard** | Opens a Gmail compose tab; the self-contained page HTML (images and CSS inlined) is injected directly into the compose body | None |
| **Notion** | Creates a new page in a Notion database with the tab's content | Notion integration token — see below |

---

## Notion Setup

1. Sign in to [Notion](https://www.notion.so/) and go to **Settings → Integrations → Develop or manage integrations → Internal**.
2. Click **+ New integration**, give it a name (e.g. "TabMit"), and enable **Read content** and **Insert content** capabilities. Click **Save**.
3. Copy the **Internal Integration Secret** (starts with `ntn_`).
4. Open the Notion database where pages should be created, click **… → Connect to** and select your integration.
5. In TabMit Settings, create a **Notion** profile, paste the token, click **Save**, then select the target database from the dropdown.

---

## Using the Extension

| Action | Chrome | Firefox |
|---|---|---|
| **Send with a specific profile** | Left-click the toolbar icon → select a profile | Left-click → ⚙ Settings; right-click the icon → select a profile from the context menu |
| **Open Settings** | Left-click → ⚙ Settings | Left-click → ⚙ Settings |
| **Send selected text only** | Select text on the page first, then invoke a profile — only the selection is used as the email body |  |

---

## Firefox Limitations

| Feature | Firefox Desktop | Firefox for Android |
|---|---|---|
| `mailto:` profiles | ✓ | Not available (Android cannot open `mailto:` URLs from extensions) |
| Gmail (plain text / clipboard) | ✓ | ✓ (untested) |
| Notion profiles | ✓ | ✓ |
| Clipboard write | ✓ | ✓ |
| Notifications | ✓ | Silently skipped (API not available) |
| Right-click context menu | ✓ | Limited (no long-press on toolbar) |

---

## Troubleshooting

| Symptom | Likely cause | Solution |
|---|---|---|
| Clicking the toolbar icon opens Settings instead of sending | No profiles configured | Add at least one profile in Settings |
| `mailto:` opens the wrong application | Wrong default mail app | Change the default mail app in your OS settings |
| "Cannot access this page" error | Trying to send from a `chrome://` or `about:` page | Navigate to a regular web page first |
| Gmail body is truncated | Page is very large; URL length cap applies | Only a truncated version can be sent; no workaround |
