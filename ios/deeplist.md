# DeepList — App Store Connect Listing Copy

Copy-paste ready fields for App Store release **1.0**.  
Each section has **English** and **繁體中文**.

> Character counts below are approximate; verify in App Store Connect before submit.

---

## App Name（名稱）

Max 30 characters.

**English**

```
DeepList
```

**繁體中文**

```
DeepList
```

---

## Subtitle（副標題）

Max 30 characters.

**English**

```
Nested lists & reminders
```

(28 characters)

**繁體中文**

```
巢狀清單與提醒待辦
```

---

## Promotional Text（宣傳文字，可選）

Max 170 characters. Shown when Apple features your app.

**English**

```
Organize life in nested lists. Add to-dos, due dates, reminders, labels, links, and attachments—all on your device.
```

**繁體中文**

```
用巢狀清單整理生活。待辦、到期日、提醒、標籤、連結與附件，資料保存在你的裝置上。
```

---

## Description（描述）

Max 4000 characters.

### English

```
DeepList is a simple, focused app for nested lists—shopping, trips, projects, movies to watch, or anything you need to break into layers.

Build outlines naturally
• Type right in the list to add or edit items
• Swipe to indent (demote) or outdent (promote) and build sub-lists
• Long-press to reorder; drag items into the order that works for you
• Open any item for full details

Stay on top of what matters
• Turn a group into To-Dos with Reminder-style checkboxes
• Set optional due dates and times
• Schedule one-time local reminders with a bell on the list
• Add labels, a URL, remarks, photos, and files

Find and review quickly
• Search across titles, remarks, URLs, and labels
• Tap a label on the list to search that tag
• Sort each sub-list manually, by due date, or by title
• Tap a link chip to open it in Safari; tap a photo to view full screen

Your data stays on your device
DeepList stores lists locally with SwiftData. No account required for everyday use.

DeepList — nested lists, without the clutter.
```

### 繁體中文

```
DeepList 是一款專注巢狀清單的 App——購物、旅行、專案、待看電影，或任何需要分層整理的事項都能輕鬆處理。

自然建立大綱
• 在清單上直接輸入即可新增或編輯
• 左右滑動縮排（降級）或取消縮排（升級），輕鬆建立子清單
• 長按進入重排，拖曳調整順序
• 點進項目即可編輯完整細節

掌握重要事項
• 將同一層設為 To-Do，使用提醒風格圓形核取框
• 可選設定到期日與時間
• 設定單次本地提醒，清單上會顯示鈴鐺
• 加上標籤、網址、備註、照片與檔案

快速搜尋與檢視
• 搜尋標題、備註、網址與標籤
• 點清單上的標籤即可用該標籤搜尋
• 每個子清單可手動排序、依到期日或依標題排序
• 點連結開啟 Safari；點照片可全螢幕檢視

資料保存在你的裝置
DeepList 使用 SwiftData 在本機儲存清單，日常使用無需帳號。

DeepList——層層清單，清晰不雜亂。
```

---

## Keywords（關鍵字）

Max 100 characters total (comma-separated, no spaces after commas preferred). Do **not** repeat the app name.

**English**

```
list,todo,checklist,reminder,nested,outline,notes,tasks,planner,organize,due date,labels
```

(≈97 characters)

**繁體中文**

```
清單,待辦,核取清單,提醒,巢狀,大綱,筆記,任務,規劃,整理,到期日,標籤
```

---

## What’s New（此版本的最新消息）

For version **1.0** (first release).

**English**

```
Welcome to DeepList 1.0!

• Nested lists with swipe indent / outdent
• To-Dos, due dates, and local reminders
• Labels, links, photos, and file attachments
• Search, sub-list sorting, and drag-to-reorder

Thanks for trying DeepList.
```

**繁體中文**

```
歡迎使用 DeepList 1.0！

• 巢狀清單，滑動縮排／取消縮排
• To-Do、到期日與本地提醒
• 標籤、連結、照片與檔案附件
• 搜尋、子清單排序與拖曳重排

感謝你試用 DeepList。
```

---

## Category（類別建議）

| Role | English | 繁體中文 |
|------|---------|----------|
| Primary | Productivity | 生產力工具 |
| Secondary | Lifestyle | 生活 |

---

## Age Rating（年齡分級說明）

- No unrestricted web browsing as core feature (links open externally when user taps)
- No user-generated public content, social, gambling, or mature themes
- **Suggested rating: 4+**

App Store Connect questionnaire: answer honestly for your build; for DeepList as shipped, expect **Ages 4+**.

---

## Copyright（版權）

```
2026 SIU LO
```

（可依實際權利人名稱調整。）

---

## App Privacy / Encryption（隱私與加密）

### Encryption (Export Compliance)

Project already sets:

`ITSAppUsesNonExemptEncryption = NO`

In App Store Connect, choose that the app **only uses exempt encryption** (e.g. HTTPS / standard OS crypto), so you can skip the full export compliance questionnaire.

### Privacy Nutrition Labels (suggested answers for current build)

Data is stored **on device** (SwiftData). Typical answers for DeepList 1.0:

| Topic | Suggested |
|-------|-----------|
| Data Linked to You | None (no account) |
| Data Used to Track You | None |
| Data Not Linked to You | None collected by the developer for analytics/ads in current build |
| Photos / Files | Used only when the user attaches them to an item; stored locally in the app |

Adjust if you later add analytics, accounts, or iCloud sync.

---

## URLs you must fill yourself

This repository does not include public pages. Replace placeholders before submit:

| Field | Placeholder |
|-------|-------------|
| Support URL | `https://YOUR_DOMAIN/support` |
| Privacy Policy URL | `https://YOUR_DOMAIN/privacy` |
| Marketing URL (optional) | `https://YOUR_DOMAIN` |

**Privacy Policy** should state at minimum:

- Lists and attachments are stored on device  
- No account required for core features  
- Local notifications for reminders  
- Photos/files access only when user adds attachments  
- Contact method for privacy questions  

---

## Localization note

- Primary locale suggestion: **English (U.S.)** with **Chinese, Traditional (Taiwan)** as additional localization (or reverse if Taiwan is primary market).
- App display name on home screen: **DeepList** (both locales).

---

## Quick checklist before submit

- [ ] Paste Name, Subtitle, Description, Keywords, What’s New (EN + 繁中 as needed)
- [ ] Set categories: Productivity / Lifestyle
- [ ] Complete age rating → expect 4+
- [ ] Encryption: exempt only (`ITSAppUsesNonExemptEncryption = NO` already in project)
- [ ] Add real Support URL + Privacy Policy URL
- [ ] Upload screenshots (6.7" / 6.5" / iPad as required)
- [ ] Build version **1.0** with App Icon 1024×1024
