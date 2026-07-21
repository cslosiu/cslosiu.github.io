# Daylog User Manual

Daylog is a simple journaling app organized by **books**. Each book is a timeline of entries you can write quickly, tag, search, and summarize.

This manual covers everyday use first, then **tags** and **tag statistics**.

---

## Getting started

1. Open Daylog.
2. You start on the **Books** screen.
3. Tap a book to open its entry timeline.
4. If you only have **one** book, Daylog opens it automatically.

On first launch, a **Default book** is created for you. That default book cannot be deleted.

Dates and times follow your device’s **locale** settings.

---

## Books

### Open a book

- Tap a book row to open it.

### Create a book

1. On **Books**, tap **+**.
2. Enter a **Book Name**.
3. Choose a **Theme Color** (affects the book tint and timeline accents).
4. Tap **Save**.

### Edit a book (name / color)

Either:

- On **Books**, **double-tap** a book, or
- Inside a book, tap **⋯** → **Edit Book**.

Change the name and/or theme color, then tap **Save**.

### Delete a book

1. On **Books**, swipe a book left.
2. Tap **Delete**, then confirm.

> The default book cannot be deleted.

---

## Writing entries

Inside a book you see a **timeline** (oldest days at the top, newest at the bottom) and a **bottom input bar**.

### Quick write (recommended)

1. Type in the bottom field (**Write something...**).
2. Optionally attach a photo/video with the **photo** button.
3. Optionally assign existing tags with **#** (see [Quick-assign tags](#quick-assign-tags-when-writing-a-new-entry)).
4. Tap the **send** (↑) button.

The list scrolls to the newest entry after you send.

> Sending requires text. You cannot send media alone.

### Keyboard

- Opening a book focuses the input bar so you can start typing right away.
- Tap the timeline (or scroll it) to dismiss the keyboard and interact with entries.
- Tap the input field again when you want to type.

### Edit an entry

Any of these:

- **Double-tap** the entry
- Swipe left → **Edit**
- Tap the **pencil** icon on the left timeline marker

In **Edit Entry** you can change:

- **Time**
- Text content
- Tags (**Tags...**)
- Photo/video attachment

Tap **Save** or **Cancel**.

### Delete an entry

- Swipe left → **Delete**.

### Photos and video

- Attach from the bottom bar (new entry) or from the editor (existing entry).
- Tap an image thumbnail on the timeline to view it full screen; tap **✕** to close.
- Video appears as a placeholder with a play icon (preview only).

---

## Timeline layout

- Entries are grouped by **day**.
- Each day has a calendar marker and a localized date.
- Each entry has a pencil marker, text, optional tags, optional media, and a time stamp.
- Day header **⋯** can export that day’s text (see [Export](#export)).

---

## Search

1. Inside a book, tap **⋯** → **Search**.
2. Type any text.

Search is **case-insensitive** and matches:

- entry content, and
- tag names on entries in **this book**.

Closing search clears the query.

---

## Export

| Action | How |
|--------|-----|
| Export the whole book as text | **⋯** → **Export text** |
| Export one day as text | Day header **⋯** → **Export day as text** |

Both open the system share sheet (Messages, Mail, Files, AirDrop, etc.).

**Day export** format example:

```text
9:34 Wake up and made breakfast.

10:58 Watched a football match.
```

(Time format follows your locale.)

### Sample data (empty books only)

If a book has **no entries**, **⋯** → **Generate random entries** creates sample timeline content for trying the UI.

---

## Tags

Tags let you label entries so you can group, search, and analyze them later.

### Where tags live

- **System tag library**: a shared list of tag names available across the app.
- **Entry tags**: the tags assigned to a specific entry.

### Create and assign tags while editing an entry

1. Open an entry (double-tap, swipe **Edit**, or tap the pencil icon on the timeline).
2. Tap **Tags...** above the text editor.
3. You can then:
   - **Tap an existing tag** to assign or unassign it (selected tags are highlighted).
   - **Type a new tag name** and tap **+** to create it and assign it to this entry.  
     The new tag is also added to the system library for next time.
   - **Remove a tag from this entry only** by tapping the **×** on the selected tag chips above the editor.
4. Tap **Save**.

### Delete a tag from the system

1. In the entry editor, open **Tags...**.
2. **Long-press** a tag in the system list.
3. Choose **Delete**, then confirm.

Deleting a system tag removes it from the library **and** from every entry that used it.

### Quick-assign tags when writing a new entry

On the book’s entry list, use the bottom input bar:

1. Tap the **#** button next to the photo button.
2. A popup lists existing system tags.
3. Tap a tag to select it (a **checkmark** appears). Tap again to unselect.
4. Selected tags appear as chips above the input field.
5. Write your text and send. The new entry is created with those tags.

> Note: the **#** popup only assigns **existing** tags. To create a brand-new tag, use the entry editor’s **Tags...** panel.

### Search by text or tags

See [Search](#search) above.

---

## Tag statistics

Statistics summarize entries **in the current book**, grouped by tag.

### Open statistics

1. Open a book (entry list).
2. Tap **⋯** → **Statistics**.

### What each row shows

Each list row is one tag (bold name on the left), with figures on the right:

| Label | Meaning |
|-------|---------|
| **cnt** | Number of entries with this tag |
| **sum** | Total of numeric entry values |
| **avg** | Average |
| **med** | Median |
| **min** | Minimum |
| **max** | Maximum |

Numbers are shown with up to **2 decimal places** (trailing zeros are omitted).

### When numbers are calculated

Numeric stats (**sum / avg / med / min / max**) are computed only when **every** entry with that tag has content that is a pure number (according to your device locale, e.g. `12.5` or `1,234`).

If any entry under that tag is not a number (for example plain text like `Had lunch`), those numeric fields show **—**.  
**cnt** is always shown.

### How tags work with statistics

Tags are the grouping key for statistics. A practical workflow:

1. Decide a tag for what you want to measure (e.g. `expense`, `weight`, `pages`).
2. For numeric analysis, write **only the number** as the entry text and assign that tag.
3. Open **Statistics** to see counts and (when all values are numeric) sum / average / median / min / max.
4. Optionally export PDF or CSV to share or keep records.

One entry can have multiple tags; it is included in the stats for **each** of its tags.

### Practical examples

**Expenses**

1. Create a tag such as `expense`.
2. For each spending entry, put only the amount in the text (e.g. `36.5`) and assign `expense`.
3. Open **Statistics** to see total spent (**sum**), average purchase (**avg**), and so on.

**Habit counts**

1. Tag entries with `workout` (content can be any text).
2. Statistics still show how many times you logged it (**cnt**).
3. Numeric fields stay **—** unless every `workout` entry is a number.

**Mixed use**

You can attach several tags to one entry. That entry is counted in the statistics for **each** of its tags.

### Export statistics

In the Statistics screen:

- **Export PDF** — creates a table PDF and opens the system share sheet.
- **Export CSV** — creates a spreadsheet-friendly CSV and opens the system share sheet.
- **Close** — dismisses the screen.

Use the share sheet to save to Files, send by Mail/Messages, AirDrop, etc.

---

## Tips

- Prefer **short, consistent tag names** (e.g. `coffee`, `expense`) so search and statistics stay clear.
- For numeric statistics, keep the entry **text as the number only**; put notes elsewhere or in another entry.
- Tags are shared across books in the system library, but **statistics and search** always apply only to the **current book**.
- Use theme colors to tell books apart at a glance.
- Use day or book text export for a quick plain-text backup or share.
