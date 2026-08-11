# AnyData 使用手冊（User Manual）

**AnyData - Design your database** 是在 iPhone / iPad 上使用的本機自訂資料庫 App。  
你可以建立多個 **Workspace**，定義 **Enumerables** 與 **Classes**，用 **Instances** / **Forms** 輸入資料，用 **Views** 篩選、關聯與彙總，並以 **ER Diagram** 檢視結構，或匯出 SQL / CSV。

資料儲存在裝置本機（SwiftData），**不需帳號**，也不會自動雲端同步。

> 畫面、按鈕與 App 內名稱（例如 `Workspaces`、`Generate Sample`、`Submit`）以**英文**呈現，與介面一致。本手冊以繁體中文說明操作。

---

## 目錄

1. [快速開始](#1-快速開始)
2. [Workspaces](#2-workspaces)
3. [Enumerables](#3-enumerables)
4. [Classes 與 Properties](#4-classes-與-properties)
5. [Instances](#5-instances)
6. [Forms](#6-forms)
7. [Views](#7-views)
8. [ER Diagram](#8-er-diagram)
9. [匯出（Export）](#9-匯出export)
10. [Generate Sample](#10-generate-sample)
11. [能力與限制](#11-能力與限制)
12. [名詞對照](#12-名詞對照)

---

## 1. 快速開始

### 建議流程

1. 開啟 App → 建立一個 **Workspace**。  
2. （可選）在空白 Workspace 點 **Generate Sample**，立刻得到示範結構與資料。  
3. 或自行：**Enumerables** → **Classes / Properties** → **Instances** 或 **Forms** → **Views**。  
4. 用 **ER Diagram** 檢查關聯；需要時用 **⋯** 選單匯出。

### 導覽結構

```
Workspaces
  └─ <Workspace>
       ├─ Enumerables
       ├─ Classes → Properties / Instances
       ├─ Views
       ├─ Forms
       ├─ Generate Sample（僅空 Workspace）
       └─ ⋯ 選單 → Export… / ER Diagram
```

---

## 2. Workspaces

**Workspace** 是一套獨立的資料空間。Enum、Class、Instance、View、Form 都屬於某個 Workspace，彼此不共用。

| 操作 | 方式 |
|------|------|
| 新增 | 在 `Workspaces` 列表點 **+** |
| 重新命名 | 依列表的編輯／選單操作（以實際介面為準） |
| 刪除 | 滑動刪除或選單刪除（會一併移除其內資料） |
| 進入 | 點 Workspace 名稱 |

---

## 3. Enumerables

**Enumerable** 是一組固定可選值（例如狀態、國家代碼清單），供 Class 屬性選用。

| 操作 | 說明 |
|------|------|
| Manage Enumerables | 建立、開啟、管理所有 Enum |
| 新增 Value | 在 Enum 編輯頁加入 case |
| 刪除 Value | 支援刪除 |
| 重複檢查 | **不允許**相同名稱的 value（去除前後空白後比對） |

---

## 4. Classes 與 Properties

**Class** 類似資料表；**Property** 是欄位。所有屬性皆為**選填**。

### 屬性類型

| 類型（UI） | 說明 |
|------------|------|
| **String** | 文字 |
| **Date/Time** | 日期＋時間 |
| **Date** | 僅日期 |
| **Time** | 僅時間 |
| **Integer** | 整數 |
| **Float** | 小數 |
| **Color** | 系統 ColorPicker；可清除為空 |
| **Enumerable** | 綁定某個 Enumerable |
| **Class** | 參考另一個 Class 的 Instance（外鍵式關聯） |

### 常見操作

1. **Manage Classes** → 新增 Class。  
2. 進入 Class → 編輯 **Properties**（名稱、類型、Enum／Class 綁定）。  
3. 需要關聯時，新增類型為 **Class** 的屬性，並指定目標 Class。

---

## 5. Instances

**Instance** 是 Class 的一筆實際資料。

1. 進入 Class → **Instances**。  
2. 點 **+** 新增一筆，或點既有列進入編輯。  
3. 依屬性類型使用對應控件（鍵盤、DatePicker、Picker、ColorPicker 等）。

刪除：在列表滑動刪除（以實際介面為準）。

> 從 View 鑽取進入的 **Record Detail** 以檢視為主；完整編輯請走 Class → Instances。

---

## 6. Forms

**Form** 是綁定單一 Class 的資料輸入介面，適合連續建檔。

### 建立 Form

1. Workspace → **Forms** → **Manage Forms** → **+**。  
2. 輸入名稱（預設會帶入所選 Class 名稱）。  
3. 選擇 **Class** → **Create**。

### 填寫

1. 從 Forms 列表或 Manage Forms 開啟 Form。  
2. 填寫各屬性。  
3. 點 **Submit**：儲存為新 Instance，並清空表單以輸入下一筆。  
4. **未 Submit 就離開**會丟棄目前草稿。

可重新命名或刪除 Form（不影響已寫入的 Instances）。

---

## 7. Views

**View** 用來查詢與瀏覽資料，支援多 Class、篩選、分組彙總。

### 建立 View

1. **Manage Views** → **+**（**New View**）。  
2. 輸入名稱。  
3. **勾選一或多個 Classes**。  
4. 選擇 **Output Columns**（顯示為 `Class › Field`；全關則輸出全部欄位）。  
5. （可選）開啟 **Group by output columns**，並新增聚合：  
   - **Count**（不需數值欄）  
   - **Sum / Average / Min / Max / Median**（需選任一已選 Class 的 Integer／Float 欄）  
6. （可選）**Filters**：AND／OR、類型化比較條件；欄位可來自任一已選 Class。  
7. **Create**。

> 建立後**不能更改 Classes**；其餘可編輯。

### 編輯既有 View

在 **Manage Views** 點 **⋯** → **Edit…**，可改：

- 名稱  
- Output columns  
- Group by／Aggregations  
- Filters  

### 執行 View

- 點 View 名稱開啟表格。  
- **有 Class 參考**的多 Class View：以 INNER JOIN 關聯。  
- **無關聯**：笛卡爾積。  
- 套用 Filters →（可選）GROUP BY 與聚合。  
- 點欄位標題排序。  
- 點 accent 色的 **Class** 值可鑽取 **Record Detail**。

### 列表副標

Workspace 與 Manage Views 列表會以小字顯示 Class、**Filter 摘要**、以及 group-by／聚合資訊。

---

## 8. ER Diagram

1. Workspace → **⋯** → **ER Diagram**。  
2. **Class** 與 **Enumerable** 以不同樣式區分；連線為 crow’s foot。  
3. 手勢：拖曳表格、雙指縮放、拖背景平移。  
4. **Auto Layout**：依螢幕寬度自動排版（最多約 3 欄），減少重疊與交叉，偏直向捲動。  
5. **Reset** 回到預設網格；**Recenter** 重設平移。  
6. **Export** PNG 或 PDF（系統分享）。

---

## 9. 匯出（Export）

Workspace → **⋯** 選單：

| 指令 | 內容 |
|------|------|
| **Export SQL DDL** | ANSI 風格 `CREATE TABLE`（含 `id` 主鍵）、外鍵、Enum 查表、`CREATE VIEW` |
| **Export Data SQL** | `INSERT` 語句 |
| **Export Data CSV** | 各表 CSV 打包為 **zip**，經系統分享面板送出 |

說明：

- 每個 Class／Enum 對應資料表；列以 Instance／case 的 **UUID** 作為 `id`（主鍵）。  
- Class／Enum 參考欄位匯出為可設外鍵的 `CHAR(36)`。  
- App 內屬性皆選填，DDL 中一般欄位為 **NULL**；`id` 為 **NOT NULL**。  
- **Median** 在核心 ANSI SQL 無標準函式，DDL View 中會以註解占位。  
- 檔案寫入 App Caches 後開啟系統分享。

---

## 10. Generate Sample

當 Workspace **完全空白**（無 Enum／Class／View／Form）時，工具列會顯示 **Generate Sample**。

會建立 Oracle **HR** 風格示範：

- Classes：Region、Country、Location、Job、Department、Employee、Job History  
- 示範 Instances（含組織層級）  
- 示範 Views（含 JOIN、篩選、GROUP BY）  
- 每個 Class 一個同名 Form  

詳見 [範例資料說明](user-guide-sample-data.md)。

---

## 11. 能力與限制

### 可以做

- 多 Workspace 本機資料庫  
- 九種屬性類型與 Class 關聯  
- Forms 連續建檔  
- 多 Class Views、Filters、GROUP BY 與聚合  
- ER Diagram 與 PNG／PDF  
- SQL DDL／INSERT／CSV 匯出  

### 目前不支援／注意

- 屬性「必填」約束（皆選填）  
- 跨 Workspace 參考  
- 雲端同步／帳號  
- View 建立後更改所選 Classes  
- Record Detail 內完整編輯（請用 Instances）  
- 匯出的 SQL 需依目標資料庫微調（目標為 ANSI 風格，非保證各引擎一鍵可跑）

---

## 12. 名詞對照

| UI / 文件用語 | 說明 |
|---------------|------|
| Workspace | 獨立資料庫空間 |
| Enumerable | 列舉／選項清單 |
| Class | 資料類型／表 |
| Property | 欄位 |
| Instance | 一筆資料 |
| Form | 依 Class 的輸入表單 |
| View | 查詢／瀏覽定義 |
| Filter | 篩選條件 |
| Group by | 分組 |
| Aggregation | Count／Sum／Avg／Min／Max／Median |
| ER Diagram | 實體關係圖 |
| Generate Sample | 產生示範資料 |

---

## 相關文件

- [App Store 送審填寫資料](app-store-submission.md)  
- [範例資料說明](user-guide-sample-data.md)  
- [資料模型（開發用）](data-model.md)  
- [UI 地圖（開發用）](ui-map.md)  

---

*本手冊對應含 Forms、多 Class Views、ER Auto Layout、SQL／CSV 匯出之功能版本。*
