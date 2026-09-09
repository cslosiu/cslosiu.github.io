# RSS Translated

A calm, private RSS reader with built-in translation. Your feeds stay on your device — no account, no sign-in.

**Privacy:** [losiu.com/ios/privacy](https://losiu.com/ios/privacy)  
**Support:** [losiu.com/ios/support](https://losiu.com/ios/support)

---

## Introduction

RSS Translated helps you follow the sites and publications you care about through standard RSS and Atom feeds. Add a website or feed URL, organize subscriptions, skim unread articles, and open any story in a clean reader. When an article is in another language, translate it with Apple’s on-device Translation — then switch back to the original whenever you like.

Everything is local-first: subscriptions, reading state, and favorites are stored on your iPhone or iPad. The app only uses the network to fetch feeds (and related images) and to run system translation when you ask for it.

### What you can do

- Add feeds from a site or feed URL (with automatic detection)
- Browse **All Articles**, **Favorites**, or a single subscription
- Filter a list to unread or favourites; search titles and article text
- Mark items read (including mark all in the current list)
- Read articles with share, open in browser, favorite, translate, and next article
- Import and export subscriptions with OPML
- Refresh one feed or all feeds

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
| **Subscriptions** | Your folders and feeds (with unread counts) |

#### Bottom toolbar

| Control | Action |
|---------|--------|
| Import | Import an OPML file of subscriptions |
| Export | Export your subscriptions as OPML |
| Refresh | Refresh all feeds |
| Settings | Open app settings |
| **+** | Add a feed |

#### Feed actions

On a feed row, use the context menu or swipe actions to:

- **Favorite / Unfavorite** the feed  
- **Refresh** that feed only  
- **Delete** the feed (and its articles)  

Folders come from OPML import (including nested folders). Feeds you add manually appear under subscriptions without a folder.

---

### Add a feed

1. Tap **+** in the sidebar.  
2. Enter a website or feed URL (for example `https://example.com`).  
3. Tap **Detect** (or press Go on the keyboard).  
4. Choose a result under **Detected Feeds**.  
5. Tap **Add**.  

The feed is saved and refreshed automatically. Use **Cancel** to close without adding.

---

### Article list

The list shows articles for the current sidebar selection. Style comes from Settings:

- **Title only** — titles only (read items appear dimmer)  
- **Preview** — title, preview text, optional image, and date  

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
| View | Choose reader font (System, Serif, Rounded, Monospaced) |
| Next | Jump to the next article in the current list |

Translation uses Apple Translation and follows your device language settings. The first use of a language pair may download a language pack. If a pair is unavailable, the app shows an error message.

---

### Settings

Open **Settings** from the sidebar gear.

**Article List**

- **List style** — Title only or Preview  
- **Preview lines** — how many lines of preview text (when Preview is selected)  

Reader font is set per session from the article **View** button, not from this screen.

---

### Refreshing feeds

- The app refreshes all feeds when it launches.  
- Use **Refresh** in the sidebar to refresh everything again.  
- Use **Refresh** on a single feed for just that source.  
- After an OPML import, feeds are refreshed automatically.  

---

### OPML import and export

- **Import** — choose an OPML (or compatible) file to bring in folders and feeds.  
- **Export** — share or save your current subscription list as OPML.  

This is the main way to set up folder structure. There is no separate “create folder” button inside the app.

---

### Privacy and data

- No account or login.  
- Subscriptions, articles, and reading state stay on your device.  
- Network is used to fetch feeds/images and for translation when you request it.  
- Standard HTTPS and Apple system frameworks only for those network features.  

More detail: [Privacy Policy](https://losiu.com/ios/privacy).  
Need help: [Support](https://losiu.com/ios/support).

---

### Tips

1. Start with one reliable feed URL (many news sites expose an RSS or Atom link).  
2. Prefer **Unread only** when catching up; use **Search** to find an older story.  
3. Star important articles or feeds so they appear under **Favorites** / **Favorite Feeds**.  
4. Use **Translate** for foreign-language posts, then **Show Original** to compare.  
5. Keep a backup of subscriptions with **Export** OPML before resetting a device.
