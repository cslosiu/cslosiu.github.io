# Views（Master / Detail）

← 返回 [使用手冊目錄](user-guide.md)

**Views** 用來以可重複使用的清單與關聯畫面瀏覽資料，不必每次從 Class 列表翻找。

目前支援兩種：

- **Master View** — 顯示某個 Class 的 Instances 清單（最多 3 個欄位）
- **Detail View** — 依附於某個 Master；顯示與「目前選取的 Master 那一列」有關連的其他 Instances

---

## 開啟 Views

在 Workspace 首頁：

- 點 **Manage Views** 進入管理畫面（標題 **Views**），或
- 直接點某個 Master 名稱開啟執行畫面

Master 快捷列副標會顯示目標 Class；若未設定則為 **No class**。

> 若 Workspace 尚無任何 Class，**New Master View** 會無法使用（disabled），請先建立 Class。

---

## 建立 Master View

1. 在 **Views** 點 **New Master View**。
2. 在 **New Master** 表單設定：

| 欄位 / 區塊 | 說明 |
|-------------|------|
| **View name** | 此 View 的名稱 |
| **Class** | 清單要顯示的目標 Class |
| **List columns (max 3)** | 點選最多三個 Properties 作為清單欄；順序即點選順序。說明文字：**Tap to select up to three properties. Order is selection order.** |
| **Filters** | 可選；限制清單顯示哪些列（見下文） |
| **Detail views** | 可選；為此 Master 附加一或多個 Detail |

3. 點 **Create**（或 **Cancel**）。

### 建立後無法再改的項目

Master 建立後：

- **可以**：**Rename**、管理 **Filters**、**Delete**
- **不可以**：變更目標 Class、變更 list columns、事後再新增 Detail View

若結構需要大改，通常需刪除後重建 Master。

---

## 新增 Detail View（僅在建立 Master 時）

在 **New Master** 表單的 **Detail views** 區塊：

1. 點 **Add Detail View**（開啟 **Add Detail**）。
2. 填寫：
   - **Detail name** — Detail 顯示名稱
   - **Link** — 選擇連結路徑（例如 `Task.Project`），代表「哪個相關 Class 的哪個 Class 類型屬性」指向 Master 的 Class
3. （可選）為該 Detail 草稿加入 Filters。
4. 點 **Add**。

若沒有任何其他 Class 具備「指向目前 Master Class」的 Class 類型屬性，會顯示：

> **No other class has a class-reference property pointing at the selected class.**

有可用連結時，footer 說明：

> **Details list related instances linked to the selected master row.**

**沒有**獨立的「New Detail View」選單；Detail 只能在建立 Master 的流程中加入。

---

## 管理既有 Views

在 **Views** 列表：

### Master

滑出或選單操作通常包含：

- **Filters…** — 開啟 Filters 管理
- **Rename** — **Rename View** 對話框
- **Delete** — 刪除 Master（其 Detail 一併移除）

副標可能包含：**No Detail**、**Details: …**、filter 數量等。

### Detail

- **Filters…**
- **Delete**
- （目前 UI **沒有** Detail 的 Rename）

副標可能顯示 **via {property}**、**No filters**、filter 數量等。

---

## 執行 Master View

開啟某個 Master 後：

- 導覽標題為 Master 名稱
- 以設定的欄位顯示 Instances（套用 Filters 後）

### 空狀態

| 情況 | 說明 |
|------|------|
| **No Class** | **This master view has no class.** |
| **No Columns** | **Select up to three properties for this master view.** |

### 點某一列（Drill-down）

| Detail 數量 | 行為 |
|-------------|------|
| 0 | 仍開啟 Detail 畫面，但只顯示該 Master Instance 的全部屬性 |
| 1 | 直接開啟該 Detail |
| 2 或更多 | 出現 **Choose Detail View**；說明為 **This master has multiple detail views.**（或類似文案），選擇後再開啟；可 **Cancel** |

---

## Detail 執行畫面（唯讀）

畫面大致分為：

1. **上方：** 選取的 Master Instance 之全部屬性（Section 標題多為 Master Class 名稱；fallback 可能為 **Record**）
2. **下方：** 依 Detail 的 link property 篩出的相關 Instances（header 為 Detail 名稱）

空狀態示例：

- **No properties**
- **No related {Class}**

相關列表中，若某欄是 Class 參照，可能以強調樣式顯示，並可繼續鑽取到其他相關畫面（依可用的 Master / Detail 設定而定）。

> Detail 畫面**不能**直接改資料。要編輯請到對應 Class 的 **Instances**。

---

## Filters

Filters 用來縮小 Master 或 Detail 顯示的資料列。可在建立時加入，或之後以 **Filters…** 管理。

### 管理畫面

- 標題：**Filters**
- **Cancel** / **Save**
- 若 View 沒有 Class：**This view has no class.**

區塊說明重點：

- Filters 為 optional
- 使用 **Match** 選擇 **AND** 或 **OR** 組合多個條件
- **不可就地編輯**既有 Filter：請刪除後再 **Add Filter**

### 新增 Filter（Add Filter）

依序設定：

1. **Field** — 選擇屬性路徑。Class 類型屬性不能當最終比對欄，需繼續鑽到葉欄位（例如經由關聯到某 String / Date）。路徑顯示以 ` › ` 連接（例如 `Prop › Nested › Leaf`）。可用 **Clear field path** 重選。選好後提示：**Field selected. Choose a comparator below.**
2. **Comparator** — 比較方式
3. **Value** — 要比對的值（視類型顯示 **Text**、**Integer**、**Number**、**Date/Time**、**Date**、**Time**、**Value** / **Select**、**Color** 等；顏色可用 **Clear color**）

點 **Add** 加入。

### 常用比較子（介面英文）

| Comparator | 說明 |
|------------|------|
| **equals** / **not equals** | 等於／不等於 |
| **>** **<** **>=** **<=** | 數值或日期時間大小比較 |
| **is null** / **not null** | 是否為空 |
| **contains** | 字串包含（**不分大小寫**）；用於 String |

不同欄位類型可用的比較子不同：例如 String 支援 contains；Enumerable / Color 主要為 equals 類與 null 類。

---

## 設計 Views 的建議

1. 先確保關聯方向正確：Detail 的 Link 必須是「子端 Class 上指向 Master Class」的屬性。
2. Master 清單欄位選最能辨識的 1～3 個欄（例如 Name、Status、Date）。
3. 需要多種關聯明細時，在建立 Master 時一次加好多個 Detail（之後無法再加）。
4. 想改欄位組合時，準備好後刪除舊 Master 再建新的。

---

## 相關章節

- [Classes 與 Properties](user-guide-classes.md)
- [Instances](user-guide-instances.md)
- [範例資料說明](user-guide-sample-data.md)
