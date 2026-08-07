# anydata 使用手冊

**anydata** 是一款在 iPhone / iPad 上使用的自訂資料庫 App。你可以在本機建立多個 **Workspace**，自行定義資料形狀（**Enumerables**、**Classes**、屬性），再錄入 **Instances**，並透過 **Master / Detail Views** 瀏覽關聯資料，或以 **ER Diagram** 檢視結構。

資料儲存在裝置本機（SwiftData），不需帳號，也不會自動雲端同步。

> UI 畫面、按鈕與 App 內建內容名稱（例如 `Workspaces`、`Generate Sample`、`Person`）一律以英文呈現，與 App 介面一致。

---

## 章節目錄

| 章節 | 說明 |
|------|------|
| [快速入門](user-guide-getting-started.md) | 核心概念、建議流程、空白 Workspace 產生範例 |
| [Workspaces](user-guide-workspaces.md) | 建立、重新命名、刪除 Workspace |
| [Enumerables](user-guide-enumerables.md) | 定義可選清單（列舉）與其 Values |
| [Classes 與 Properties](user-guide-classes.md) | 定義資料結構與屬性類型 |
| [Instances](user-guide-instances.md) | 新增與編輯實際資料列 |
| [Views](user-guide-views.md) | Master / Detail 瀏覽、Filters、鑽取 |
| [ER Diagram](user-guide-er-diagram.md) | 實體關係圖與匯出 |
| [範例資料說明](user-guide-sample-data.md) | `Generate Sample` 會建立什麼 |

---

## 核心概念一覽

| 概念 | 用途 |
|------|------|
| **Workspace** | 一組獨立的資料庫空間；Enum、Class、View 都屬於某個 Workspace |
| **Enumerable** | 一組固定可選值（例如狀態、角色），供屬性選用 |
| **Class** | 一筆資料的「類型／表格」定義（例如 Person、Project） |
| **Property** | Class 上的欄位；皆為選填 |
| **Instance** | Class 的一筆實際資料 |
| **Master View** | 以清單顯示某 Class 的 Instances（最多 3 個欄位） |
| **Detail View** | 依附於 Master；顯示與選取列關聯的其他 Class Instances |
| **Filter** | 限制 Master 或 Detail 顯示哪些資料列 |
| **ER Diagram** | 以圖表呈現該 Workspace 的 Classes、Enumerables 與關聯 |

---

## 導覽結構

```
Workspaces
  └─ <Workspace 名稱>
       ├─ Enumerables  → Manage Enumerables / 個別 Enumerable
       ├─ Classes      → Manage Classes / 個別 Class
       │                    ├─ Properties（Schema）
       │                    └─ Instances
       ├─ Views        → Manage Views / 開啟 Master View
       ├─ Generate Sample（僅空 Workspace）
       └─ ER Diagram
```

---

## 建議使用順序

1. 建立一個 **Workspace**。
2. （可選）先定義會重複使用的 **Enumerables**。
3. 建立 **Classes**，並在 **Properties** 中加入欄位；需要關聯時使用 `Class` 類型屬性。
4. 在 **Instances** 中錄入資料。
5. 建立 **Master View**（必要時一併加入 Detail Views 與 Filters）。
6. 用 **ER Diagram** 檢查結構，或匯出圖表。

若想先體驗完整範例，可在空白 Workspace 點 **Generate Sample**（詳見 [範例資料說明](user-guide-sample-data.md)）。

---

## 能力與限制（摘要）

**可以做的事**

- 多個 Workspace；各自獨立的 Enum / Class / Instance / View
- 九種屬性類型：String、Date/Time、Date、Time、Integer、Float、Color、Enumerable、Class
- Master / Detail 瀏覽與 Filters（AND / OR）
- ER Diagram 匯出為 PNG 或 PDF

**目前不支援**

- 必填屬性、多值／清單欄位
- 跨 Workspace 參照
- 雲端同步、一般資料匯入／匯出、查詢語言、權限
- 在 Detail 執行畫面內直接編輯 Instance（請到 Class → Instances）
- Master 建立後變更目標 Class 或清單欄位；建立後無法再從 UI 新增 Detail View
- Filters 就地編輯（請刪除後重新新增）

詳細操作請見各章節。
