# 範例資料說明（Generate Sample）

← 返回 [使用手冊目錄](user-guide.md)

當 Workspace 內 **沒有任何** Enumerable、Class、View 時，工具列會出現 **Generate Sample**。點一下即可建立一套示範用的專案／任務／採購資料，方便立刻體驗 Views 與關聯。

> 若已手動建立過任何 Enum / Class / View，按鈕不會出現。需要範例時請開一個全新的空 Workspace。

以下名稱皆與 App 內實際內容一致（英文）。

---

## Enumerables

| Enumerable | Values |
|------------|--------|
| **Role** | Boss, Manager, Programmer |
| **Task Status** | To Do, In Progress, Done |
| **Order Status** | Pending, Approved, Rejected |
| **Milestone Status** | Planned, Reached, Missed |

---

## Classes 與 Properties

| Class | Properties（名稱 · 類型／綁定） |
|-------|--------------------------------|
| **Person** | Name (String), Role (Enumerable → Role), Email (String), Hire Date (Date) |
| **Company** | Name (String), City (String) |
| **Product** | Name (String), Vendor (Class → Company), Unit Price (Float) |
| **Project** | Name (String), Code (String), Start Date (Date), Color (Color), Lead (Class → Person) |
| **Task** | Title (String), Project (Class → Project), Assignee (Class → Person), Due Date (Date), Status (Enumerable → Task Status) |
| **Milestone** | Name (String), Project (Class → Project), Date, Review Time (Time), Status (Enumerable → Milestone Status) |
| **Purchase Order** | Order Number (String), Manager (Class → Person), Vendor (Class → Company), Product (Class → Product), Amount (Float), Status (Enumerable → Order Status), Submitted At (Date/Time), Decided At (Date/Time), Approver (Class → Person) |

---

## 樣本資料規模（約）

| Class | 約略筆數 / 內容 |
|-------|-----------------|
| **Person** | 1 位 Boss、2 位 Manager、4 位 Programmer |
| **Company** | 3 |
| **Product** | 4 |
| **Project** | 3（例如 Atlas Mobile、Orion API、Nova Portal） |
| **Task** | 9 |
| **Milestone** | 4 |
| **Purchase Order** | 4（例如 PO-1001 … PO-1004） |

實際姓名與欄位值以 App 產生結果為準。

---

## 預建 Master Views

| Master View | 清單欄位（概念） | Detail Views |
|-------------|------------------|--------------|
| **Projects** | Name, Code, Start Date | **Tasks**、**Milestones**（經由指向 Project 的連結） |
| **Purchase Orders** | Order Number, Amount, Status | 無 |
| **Team** | Name, Role, Hire Date | 無 |

建議體驗路徑：

1. 開啟 **Projects** → 點某一專案列 → 在 **Choose Detail View**（若出現）選 **Tasks** 或 **Milestones**。
2. 開啟 **Purchase Orders** 查看篩選前的採購清單欄位。
3. 開啟 **Team** 查看人員 Role 與 Hire Date。
4. 回到 Workspace 點 **ER Diagram** 檢視整體關係。

---

## 相關章節

- [快速入門](user-guide-getting-started.md)
- [Views](user-guide-views.md)
- [ER Diagram](user-guide-er-diagram.md)
