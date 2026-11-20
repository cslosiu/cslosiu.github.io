# Lab Report User Manual / 檢驗報告使用手冊

**App:** Lab Report / 檢驗報告 / 检验报告  
**Bundle ID:** `com.losiu.labreport.app`

This document is bilingual: **English** first, then **繁體中文**.

---

## English

### What this app does

Lab Report is a **local-only** iOS app for personal lab-value tracking. There is no account and no cloud sync. Values stay on your device. It is **not medical advice**.

### Main tabs

1. **Browse** — Categories and items (English + Chinese names). Open an item for history and a trend chart. You can multi-select compatible items and open a compare chart.
2. **Entry** — Pick a date and enter values for many items at once. One value per item per calendar day (saving again updates that day).
3. **Manage** — Edit or delete categories and items, including seed data. Adjust reference ranges to match your lab report.
4. **Settings** — Export / import CSV, export a category–item catalog, and view version / disclaimer.

### Units and reference ranges

- Each item has a **canonical unit** and optional alternate units with linear conversion.
- Entered values are stored in the canonical unit; the chart and history can show the unit you prefer.
- Default reference ranges are illustrative. Edit them under Manage to match your report.

### CSV: records export / import

#### Format

- Encoding: **UTF-8 with BOM** (Excel-friendly for Chinese).
- All fields are **always quoted**.
- Header row (same for export and import):

```text
"date","category_en","category_local","item_en","item_local","value_canonical","canonical_unit","value_input","input_unit","reference_low","reference_high","note","updated_at"
```

| Column | Required for import? | Notes |
|--------|----------------------|--------|
| `date` | Yes | `yyyy-MM-dd` (calendar day) |
| `category_en` | Optional | English category name; if present, must match with `item_en` |
| `item_en` | Yes | English item name — **match key** |
| `value_input` + `input_unit` | Preferred | Display value + unit symbol known to the item |
| `value_canonical` | Fallback | Used if input value is empty |
| `note` | Optional | Free text |
| Other columns | Ignored on import | Exported for readability |

#### Matching rules

- Match **item** and **category** by **English name** (`item_en`, `category_en`).
- Comparison is **case-insensitive** and **trims spaces**.
- If `category_en` is provided, the item must belong to that category.
- Same **item + date**: **later rows in the file win** (one value per item per day).

#### How to export / import

1. **Settings → Export CSV** — share or save the records file.
2. **Settings → Import CSV** — pick a file in the same format.
3. After import, the app shows added / updated / skipped counts and any unmatched English item names.

Tip: export once, edit in a spreadsheet that keeps UTF-8, then re-import.

### CSV: categories & items catalog

**Settings → Export Categories & Items CSV** writes a reference list (not records):

```text
"category_en","category_zh_hant","category_zh_hans","item_en","item_zh_hant","item_zh_hans","canonical_unit"
```

Use this to look up valid English names before building an import file. Importing this catalog does **not** create items; only the records CSV imports values into existing items.

### Privacy

All data is stored on-device with SwiftData. No login. CSV files you export may contain personal health information — share them carefully.

---

## 繁體中文

### 這個 App 做什麼

「檢驗報告」是**僅本機**的 iOS App，用來追蹤個人檢驗數值。沒有帳號、沒有雲端同步，資料留在裝置上。**非醫療建議**。

### 主要分頁

1. **瀏覽** — 依類別／項目查看（中英名稱）。開啟項目可看歷史與趨勢圖；可多選相容項目開啟比較圖表。
2. **輸入** — 選日期一次輸入多個項目。同一項目同一天只有一筆（再存會覆寫）。
3. **管理** — 編輯或刪除類別與項目（含預設種子資料），並調整參考範圍以符合你的報告。
4. **設定** — 匯出／匯入 CSV、匯出類別與項目清單、查看版本與免責聲明。

### 單位與參考範圍

- 每個項目有**標準單位**與可選的換算單位（線性換算）。
- 數值以標準單位儲存；顯示時可改用你習慣的單位。
- 預設參考範圍僅供示意，請在「管理」中依報告自行修改。

### CSV：紀錄匯出／匯入

#### 格式

- 編碼：**UTF-8（含 BOM）**，方便 Excel 正確開啟中文。
- **所有欄位一律加雙引號**。
- 表頭（匯出與匯入相同）：

```text
"date","category_en","category_local","item_en","item_local","value_canonical","canonical_unit","value_input","input_unit","reference_low","reference_high","note","updated_at"
```

| 欄位 | 匯入是否必要 | 說明 |
|------|--------------|------|
| `date` | 是 | `yyyy-MM-dd`（日曆日） |
| `category_en` | 選填 | 英文類別名；若有填，須與 `item_en` 對應 |
| `item_en` | 是 | 英文項目名 — **匹配鍵** |
| `value_input` + `input_unit` | 建議 | 輸入值 + 項目支援的單位符號 |
| `value_canonical` | 備援 | 若輸入值空白則使用 |
| `note` | 選填 | 備註 |
| 其他欄位 | 匯入時忽略 | 匯出供閱讀 |

#### 匹配規則

- 以**英文名稱**匹配項目／類別（`item_en`、`category_en`）。
- **不分大小寫**，並會**去除前後空白**。
- 若有填 `category_en`，該項目必須屬於該類別。
- 同一**項目 + 日期**：檔案中**較後面的列覆寫前面的**（一天一值）。

#### 操作方式

1. **設定 → 匯出 CSV** — 分享或儲存紀錄檔。
2. **設定 → 匯入 CSV** — 選擇相同格式的檔案。
3. 匯入後會顯示新增／更新／跳過筆數，以及未匹配的英文項目名。

建議：先匯出一份，用能保留 UTF-8 的試算表編輯後再匯入。

### CSV：類別與項目清單

**設定 → 匯出類別與項目 CSV** 會輸出參考清單（不是檢驗紀錄）：

```text
"category_en","category_zh_hant","category_zh_hans","item_en","item_zh_hant","item_zh_hans","canonical_unit"
```

用來查詢有效的英文名稱以便製作匯入檔。此清單**不會**用來建立項目；只有「紀錄 CSV」會把數值寫入既有項目。

### 隱私

資料以 SwiftData 存在裝置上，無需登入。你匯出的 CSV 可能含個人健康資訊，請謹慎分享。
