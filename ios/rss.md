# RSS Translated

A calm, private RSS reader built for cross-language reading: on-device translation, article summarization, list auto-summary, and topic digests. Your feeds stay on your device — no account, no sign-in.

**Product:** [losiu.com/ios/rss](https://losiu.com/ios/rss)  
**Privacy:** [losiu.com/ios/privacy](https://losiu.com/ios/privacy)  
**Support:** [losiu.com/ios/support](https://losiu.com/ios/support)

---

## Introduction

RSS Translated helps you follow the sites and publications you care about through standard RSS and Atom feeds. Add a website or feed URL, organize subscriptions in folders, and skim unread stories in a clean three-pane layout (sidebar, article list, and reader).

What makes it different is how it handles language and length **on your device**:

- **Translate** full articles with Apple Translation (using language packs already installed on the device).
- **Summarize** long posts into a short on-device summary (Apple Intelligence when available; otherwise Natural Language analysis), shown as a banner in the reader and optionally in a summary sheet.
- **Auto summary** in the article list — new items can be summarized and translated in the background so you can skim in your language without opening every story.
- **Topic digests** — the app periodically folds related articles into longer essays stored locally, with optional translation.

Everything is local-first: subscriptions, reading state, favorites, summary caches, and digests live on your iPhone or iPad. The network is used to fetch feeds and images, and for on-device translation when a language pair is already available. Both HTTP and HTTPS feed URLs are supported.

### What you can do

- Add feeds from a site or feed URL (with automatic detection), optionally into a folder
- Share a webpage from Safari or other apps to open **Add Feed** with the site host filled in
- Browse **All Articles**, **Favorites**, a folder, or a single subscription; open **Topics** for digests
- Search feeds by name or URL; search articles by title and content
- Filter a list to unread or favourites; mark all items in the current list as read
- Choose list style: **Auto summary** (default), **Preview**, or **Title only**
- Auto-summarize and translate new articles in the list (optional; cached on device by language)
- Summarize in the reader (banner + sheet); translate summaries and full articles
- Customize reader fonts — title, body, and the summary banner follow the same family (banner at a relative size)
- Tap article images for a full-screen viewer (zoom and share)
- Run topic digests on an interval or on demand; read stored essays (translated when available)
- Import OPML from Files or a web URL; export OPML
- View feed info, move feeds between folders, and inspect refresh errors
- On first launch with no subscriptions, load curated **Sample Feeds** automatically

---

## User Manual

### Main layout

On larger screens the app uses three columns (stacked navigation on iPhone):

1. **Sidebar** — smart lists, subscriptions, and Topics  
2. **Article list** (or a topic digest placeholder) — stories for the current selection  
3. **Reader** — the article or digest essay you selected  

Tap a sidebar item to change the list. Opening an article marks it as read.

---

### Sidebar

Navigation title: **RSS Translated**.

| Item | Purpose |
|------|---------|
| **All Articles** | Every article from all feeds |
| **Favorites** | Articles you starred |
| **Favorite Feeds** | Feeds you marked as favourite (only when you have some) |
| **Subscriptions** | Folders and feeds with unread counts (case-insensitive name order) |
| **Topics** | Topic digests (when digests exist, a run is in progress, or a run has completed before) |

While searching feeds, smart lists and Topics are hidden so you can focus on matching subscriptions.

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Import and Export | **Import from Files**, **Import from URL**, **Export OPML**, then **Update Topic Digests** |
| Search | Show a search field above the feed list (`Search feeds`) |
| Refresh All | Refresh every subscription |
| Settings | Open app settings |
| **+** | Add a feed |

**Feed search** matches titles and feed URLs. Matching feeds inside folders expand those folders automatically. Tap Search again to hide the bar. Empty results: **No Results**.

#### Folders and feeds

- Tap a **folder name** to show all articles from feeds in that folder and its nested folders (newest first).  
- Use the chevron to expand or collapse the folder without changing the selection.  
- Unread counts on folders include nested feeds.

On a feed row (context menu or swipe):

- **Feed Info** — title, URLs, last fetch, unread count, and folder (move or create a folder)  
- **Add Favorite** / **Remove Favorite**  
- **Refresh** that feed only  
- **Delete** the feed and its articles  

If a refresh fails, an orange warning appears on the row. Tap it for **Refresh Error**, then **Close** or **Delete**.

Folders come from OPML import (including nesting), **Add Feed** / **Feed Info**, or the automatic **Sample Feeds** folder. Feeds without a folder sit directly under **Subscriptions**.

#### Topics

Digests are grouped by tag. Expand a tag to see essay rows (date and article count).

- While a run is in progress, status text appears **under the Topics header** (for example `Updating topic digests…` or `Digesting: …`).  
- The section footer shows **Last digest** date/time, or **No digests yet**.  

Open an essay to read it. The app prefers a stored translation when present; otherwise it shows the source-language essay and offers **Translate**.

#### Sample Feeds

With no subscriptions yet, the app seeds a **Sample Feeds** folder from a curated public list and refreshes those feeds. Treat them like any other subscription (favorite, move, or delete).

---

### Add a feed

1. Tap **+** in the sidebar.  
2. Enter a website or feed URL (placeholder `https://example.com`).  
3. Tap **Detect** (or Go on the keyboard).  
4. Choose a result under **Detected Feeds**.  
5. Optionally set **Add to**: **No Folder**, an existing folder, or **New Folder**.  
6. Tap **Add**.  

The feed is saved and refreshed immediately. **Cancel** closes without adding.

#### Share from another app

1. In Safari (or another app), share a webpage URL.  
2. Choose **RSS Translated** in the system share sheet.  
3. Confirm **Open in RSS Translated**.  
4. **Add Feed** opens with the site **hostname** filled in — then Detect / Add as usual.

---

### Article list

Style comes from **Settings → List style**:

| List style | What you see |
|------------|----------------|
| **Auto summary** (default) | Title plus on-device summary (translated summary preferred when cached). Until a summary exists, a short content preview may show as a stand-in. Optional thumbnail and date. |
| **Preview** | Title, a few lines of feed/content preview (**Preview lines**), optional thumbnail, and date |
| **Title only** | Titles only (read items appear dimmer); no thumbnail or date |

**Background list summarization** runs only when **Auto-summarize feeds** is on **and** list style is **Auto summary**. It targets articles that are not yet summarized (after launch and after feed refresh), with limited concurrency. Cached summaries stay when you switch to Preview or Title only; clear them in Settings when you want to free space or regenerate.

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Show All | Clear list filters |
| Show Unread Only | Only unread articles in this list |
| Show Favourite in This List | Only favourited articles in this list |
| Mark All Read | Confirm, then mark every article in the current scope as read |
| Search | Search field (`Search titles and articles`) |

Search matches title, preview, list summary, and article body/HTML fields. Changing the sidebar selection resets filters and search.

**Pull to refresh** is available when viewing a **single feed**.

Empty list: **No Articles**. No search hits: **No Results**.

---

### Reading an article

Opening an article marks it as read. The reader may show an **automatic summary** banner at the top (cached summary, or while a fresh summary is generated for this article). Labels: **Automatic summary** or **Automatic summary translated**; loading shows **Summarizing…**.

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Open & Share | **Open in Browser** or **Share** the article link |
| Summarize | Open the **Summary** sheet (generates a summary if needed) |
| Favorite / Unfavorite | Star or unstar the article |
| Translate / Show Original | Translate title and body, or switch back |
| View | **View Settings** for font and size |
| Next | Next article in the current list order |

The **Summary** sheet shows the summary text, sentence count, and backend name (**Apple Intelligence** or **On-device language analysis**), and may include a **Translation** section when a translated summary is available.

Tap the hero image for a full-screen viewer: **Close**, pinch to zoom, and **Share**. (Saving to Photos is not offered.)

#### View Settings

- **Font** — choose a system font, or **Use System Font**  
- **Use System Text Size** — follow Dynamic Type (default on)  
- **Font Size** — 10–25 when system size is off (default 17)  

These settings apply to the article title and body, and to the **summary banner** (same family; banner text stays relatively smaller than body text).

Translation uses Apple’s on-device Translation with **already installed** language pairs. If a pair is unavailable, the app shows an error rather than prompting to download packs from the reader flow.

---

### Settings

Open **Settings** from the sidebar gear, then **Done** to close.

#### Article List

- **List style** — Auto summary, Preview, or Title only (default: Auto summary)  
- **Preview lines** — 1–10 (default 3); only shown when Preview is selected  
- **Show article thumbnails** — default on  

#### Summarize

- **Auto-summarize feeds** — allow background list summarization (default on; also requires Auto summary list style)  
- **Summary sentences** — target length (default 3; range 1–10)  
- **Summarized articles** / **Translated summaries** — cache counts  
- **Clear Cached Summaries** — remove stored summaries and translations to free space (they can be regenerated later)  

Turning Auto-summarize off, or switching list style away from Auto summary, stops the background pipeline but does not delete existing caches.

#### Topic Digests

- **Digest max words** — target essay length (default 200; 100–1000)  
- **Auto-update every N day(s)** — interval between automatic runs (default 7; 1–30)  

Reader fonts are configured from the article **View** button, not here.

---

### Refreshing feeds

- Feeds refresh on launch and when returning to the foreground (with a short cooldown so servers are not hammered).  
- **Refresh All** in the sidebar refreshes every subscription.  
- **Refresh** on a single feed (or pull to refresh on that feed’s list) updates one source.  
- After OPML import or Sample Feeds seeding, feeds refresh automatically.  
- When Auto summary is enabled, unsummarized articles are queued after launch/refresh for background summary (and silent translation when the language pair is installed).  

---

### Topic digests

Topic digests combine recent articles into longer essays stored on device (`DigestedTag` / `DigestEssay`).

- **Automatic:** first run when no digests exist yet; later runs after the interval in Settings. Also considered on launch and when returning to the foreground.  
- **Manual:** Import and Export → **Update Topic Digests** (disabled while a run is in progress).  
- Progress appears as caption text under the **Topics** header; the footer shows the last successful run time.  
- Essays are stored even if translation fails; translate later from the digest reader.  

---

### OPML import and export

From **Import and Export**:

- **Import from Files** — pick an OPML (or compatible) file.  
- **Import from URL** — paste a link to an OPML file, then Import.  
- **Export OPML** — share or save your subscription list (default name `rss-translated-subscriptions`).  

Use **Feed Info** or **Add Feed** to place feeds in folders without re-importing.

---

### Privacy and data

- No account or login.  
- Subscriptions, articles, reading state, favorites, summary caches, and digests stay on your device.  
- Network is used to fetch feeds and images, and for on-device translation when a language pair is already installed.  
- Standard HTTPS and Apple system frameworks only (export compliance: non-exempt encryption not used).  

More detail: [Privacy Policy](https://losiu.com/ios/privacy).  
Need help: [Support](https://losiu.com/ios/support).

---

### Tips

1. On a fresh install, try **Sample Feeds**, then keep or remove what you like.  
2. Share a site from Safari into RSS Translated when you discover something new.  
3. Keep **Auto summary** for a translated skim of the list; switch to **Preview** for raw content snippets.  
4. Use **Show Unread Only** when catching up; use article or feed **Search** to find older items or subscriptions.  
5. Star important articles or feeds for **Favorites** / **Favorite Feeds**.  
6. In the reader, use **Summarize** and **Translate**, then **Show Original** to compare.  
7. Run **Update Topic Digests** after catching up on several feeds.  
8. Use **Clear Cached Summaries** if you need space or want fresh summaries.  
9. Export OPML before resetting a device so you can restore subscriptions quickly.
