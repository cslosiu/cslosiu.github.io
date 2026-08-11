# 快速入門

← 返回 [使用手冊目錄](user-guide.md)

本頁說明如何在幾分鐘內開始使用 **anydata**。

---

## 開啟 App 之後

App 啟動後會進入 **Workspaces** 清單。每個 Workspace 是一套獨立的自訂資料庫。

1. 點右上角 **Add Workspace**。
2. 在 **New Workspace** 對話框輸入 **Name**，再點 **Create**。
3. 點進該 Workspace，進入 Workspace 首頁。

Workspace 首頁分為三個區塊：

- **Enumerables** — 管理可選值清單
- **Classes** — 管理資料類型與 Instances
- **Views** — 管理與開啟瀏覽用 Views

工具列另有：

- **Generate Sample** — 僅在此 Workspace 尚無任何 Enum、Class、View 時顯示
- **ER Diagram** — 開啟實體關係圖

---

## 兩種開始方式

### A. 使用範例資料（最快）

1. 建立空的 Workspace（不要先手動加 Enum / Class / View / Form）。
2. 點 **Generate Sample**。
3. App 會建立 Oracle HR 風格的 Classes、實例資料、示範 Views，以及每個 table 的 Form。
4. 從 **Views** 開 **Employee Directory** 或 **Salary by Department**；或從 **Forms** 開 **Employee** 新增資料。

範例內容細節見 [範例資料說明](user-guide-sample-data.md)。

### B. 從頭自訂

建議順序：

1. （可選）在 **Manage Enumerables** 建立狀態、角色等清單。
2. 在 **Manage Classes** 建立 Class，並到 **Properties** 加入欄位。
3. 需要「指向另一個 Class 的某一筆」時，屬性類型選 **Class**。
4. 到 **Instances** 新增資料列。
5. 在 **Manage Views** 建立 **New Master View**，設定清單欄位與（可選）Detail / Filters。

---

## 名詞對照（閱讀指南用）

| 你可能熟悉的概念 | 在 anydata 中 |
|------------------|---------------|
| 資料庫／專案空間 | Workspace |
| 下拉選項／列舉 | Enumerable + Values |
| 資料表／實體類型 | Class |
| 欄位 | Property |
| 一列資料／紀錄 | Instance |
| 清單畫面 | Master View |
| 主從／關聯明細 | Detail View |
| 篩選條件 | Filter |

介面上的標籤一律使用英文欄中的名稱。

---

## 下一步

- [Workspaces](user-guide-workspaces.md)
- [Enumerables](user-guide-enumerables.md)
- [Classes 與 Properties](user-guide-classes.md)
- [Instances](user-guide-instances.md)
- [Views](user-guide-views.md)
