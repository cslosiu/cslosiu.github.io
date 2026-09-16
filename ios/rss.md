# RSS Translated

A calm, private RSS reader with built-in translation. Your feeds stay on your device — no account, no sign-in.

**Product:** [losiu.com/ios/rss](https://losiu.com/ios/rss)  
**Privacy:** [losiu.com/ios/privacy](https://losiu.com/ios/privacy)  
**Support:** [losiu.com/ios/support](https://losiu.com/ios/support)

---

## Introduction

RSS Translated helps you follow the sites and publications you care about through standard RSS and Atom feeds. Add a website or feed URL, organize subscriptions in folders, skim unread articles, and open any story in a clean reader. When an article is in another language, translate it with Apple’s on-device Translation — then switch back to the original whenever you like.

Everything is local-first: subscriptions, reading state, and favorites are stored on your iPhone or iPad. The app only uses the network to fetch feeds (and related images) and to run system translation when you ask for it. Both HTTP and HTTPS feed URLs are supported.

### What you can do

- Add feeds from a site or feed URL (with automatic detection), optionally into a folder
- Share a webpage from Safari or other apps to open **Add Feed** with the site host filled in
- Browse **All Articles**, **Favorites**, a folder, or a single subscription
- Search the feed list by name or feed URL; search the article list by title and content
- Filter a list to unread or favourites; mark items read (including mark all in the current list)
- Read articles with share, open in browser, favorite, translate, adjustable fonts, and next article
- Tap article images to view them full screen (zoom, share, or save)
- Import OPML from Files or a web URL; export OPML
- View feed info, move feeds between folders, and see refresh errors when a feed fails
- On first launch with no subscriptions, load curated **Sample Feeds** automatically

---

## User Manual

### Main layout

The app uses three columns on larger screens (and stacked navigation on iPhone):

1. **Sidebar** — subscriptions and smart lists  
2. **Article list** — stories for the current selection  
3. **Reader** — the article you selected  

Tap a sidebar item to change which articles appear in the list. Tap a row to read it (opening an article marks it as read).

---

### Sidebar

| Item | Purpose |
|------|---------|
| **All Articles** | Every article from all feeds |
| **Favorites** | Articles you starred |
| **Favorite Feeds** | Feeds you marked as favourite (shown only when you have some) |
| **Subscriptions** | Your folders and feeds (with unread counts), sorted case-insensitively by name |

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Import / Export | Menu: **Import from Files**, **Import from URL**, or **Export OPML** |
| Search | Show a search field above the feed list |
| Refresh | Refresh all feeds |
| Settings | Open app settings |
| **+** | Add a feed |

**Feed search** matches feed titles and feed URLs as you type. Matching feeds inside folders expand those folders automatically. Tap Search again to hide the bar.

#### Feed actions

On a feed row, use the context menu or swipe actions to:

- **Feed Info** — title, URLs, last fetch, unread count, and folder (move or create a folder)  
- **Favorite / Unfavorite** the feed  
- **Refresh** that feed only  
- **Delete** the feed (and its articles)  

If a refresh fails, an warning icon appears on the feed row. Tap it to read the error and dismiss or delete the feed.

Folders can come from OPML import (including nested folders), from **Add Feed** / **Feed Info** when you choose a new or existing folder, or from the automatic **Sample Feeds** folder on first launch. Feeds without a folder appear directly under **Subscriptions**.

#### Sample Feeds

If you open the app with no subscriptions yet, RSS Translated loads a starter set of public feeds into a **Sample Feeds** folder and refreshes them. You can favorite, move, or delete those feeds like any other subscription.

---

### Add a feed

1. Tap **+** in the sidebar.  
2. Enter a website or feed URL (for example `https://example.com`).  
3. Tap **Detect** (or press Go on the keyboard).  
4. Choose a result under **Detected Feeds**.  
5. Optionally assign a folder: **No Folder**, an existing folder, or **New Folder**.  
6. Tap **Add**.  

The feed is saved and refreshed automatically. Use **Cancel** to close without adding.

#### Share from another app

1. In Safari (or another app), share a webpage URL.  
2. Choose **RSS Translated** in the system share sheet.  
3. The app opens **Add Feed** with the site’s host (hostname only) in the URL field — then Detect / Add as usual.

---

### Article list

The list shows articles for the current sidebar selection. Style comes from Settings:

- **Title only** — titles only (read items appear dimmer)  
- **Preview** — title, preview text, optional thumbnail, and date  

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Show all | Clear list filters |
| Show unread only | Only unread articles in this list |
| Show favourite in this list | Only favourited articles in this list |
| Mark all read | Confirm, then mark every article in the current scope as read |
| Search | Show a search field above the list |

**Search** matches text in titles and article content. Tap Search again to hide the bar; pressing Return on an empty search field also closes it.

Changing the sidebar selection resets filters and search for that list.

---

### Reading an article

Select an article to open the reader. Use the bottom toolbar:

| Control | Action |
|---------|--------|
| Open in Browser | Open the article link in Safari / default browser |
| Share | Share the title and link via the system share sheet |
| Favorite | Star or unstar the article |
| Translate | Translate into your preferred language, or **Show Original** to switch back |
| View | Open **View Settings** for font and size |
| Next | Jump to the next article in the current list |

If the article has a main image, tap it to open a full-screen viewer with zoom, share, and save to Photos (permission is requested when you save).

#### View Settings

- **Font** — pick any system font (or **Use System Font**)  
- **Use System Text Size** — follow Dynamic Type when on  
- **Font Size** — custom size from 10 to 25 when system size is off  

These preferences are remembered for the reader.

Translation uses Apple Translation and follows your device language settings. The first use of a language pair may download a language pack. If a pair is unavailable, the app shows an error message.

---

### Settings

Open **Settings** from the sidebar gear.

**Article List**

- **List style** — Title only or Preview  
- **Preview lines** — how many lines of preview text (when Preview is selected)  
- **Show article thumbnails** — show or hide the article image thumbnail in Preview mode  

Reader font and size are set from the article **View** button, not from this screen.

---

### Refreshing feeds

- The app refreshes feeds when it launches (and when returning to the foreground, with a short cooldown so servers are not hammered).  
- Use **Refresh** in the sidebar to refresh everything again.  
- Use **Refresh** on a single feed for just that source.  
- After an OPML import or Sample Feeds seed, feeds are refreshed automatically.  

---

### OPML import and export

Open the **Import / Export** menu in the sidebar:

- **Import from Files** — pick an OPML (or compatible) file to bring in folders and feeds.  
- **Import from URL** — paste a link to an OPML file on the web, then Import.  
- **Export OPML** — share or save your current subscription list as OPML.  

Use **Feed Info** or **Add Feed** to place feeds in folders without re-importing OPML.

---

### Privacy and data

- No account or login.  
- Subscriptions, articles, and reading state stay on your device.  
- Network is used to fetch feeds/images and for translation when you request it.  
- Standard HTTPS and Apple system frameworks only for those network features (export compliance: non-exempt encryption not used).  

More detail: [Privacy Policy](https://losiu.com/ios/privacy).  
Need help: [Support](https://losiu.com/ios/support).

---

### Tips

1. On a fresh install, try **Sample Feeds**, then keep or remove what you like.  
2. Share a site from Safari into RSS Translated when you discover something new.  
3. Prefer **Unread only** when catching up; use article **Search** to find an older story, or feed **Search** to find a subscription.  
4. Star important articles or feeds so they appear under **Favorites** / **Favorite Feeds**.  
5. Use **Translate** for foreign-language posts, then **Show Original** to compare.  
6. Turn off **Show article thumbnails** in Settings for a denser Preview list.  
7. Keep a backup of subscriptions with **Export OPML** before resetting a device.
