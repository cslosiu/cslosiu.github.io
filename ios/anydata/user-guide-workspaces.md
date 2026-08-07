# Workspaces

← 返回 [使用手冊目錄](user-guide.md)

**Workspace** 是 anydata 的頂層容器。一個 Workspace 內的 Enumerables、Classes、Instances、Views 彼此共用，但不會與其他 Workspace 互相參照。

---

## 開啟 Workspaces 清單

App 首頁標題為 **Workspaces**。列表顯示每個 Workspace 的名稱與建立日期。

---

## 新增 Workspace

1. 點工具列 **Add Workspace**（加號）。
2. 在 **New Workspace** 對話框的 **Name** 欄位輸入名稱。
3. 點 **Create**；若要放棄則點 **Cancel**。

---

## 重新命名

1. 在列表向左滑該列，點 **Rename**。
2. 在 **Rename Workspace** 對話框修改名稱。
3. 點 **Save**，或 **Cancel** 取消。

---

## 刪除

在列表向左滑該列，使用系統刪除手勢刪除 Workspace。

> 刪除 Workspace 會一併移除其內所有 Enum、Class、Instance、View。請確認後再刪。

---

## 進入 Workspace

點列表中的某一列，進入該 Workspace 首頁。導覽標題為 Workspace 的名稱。

首頁內容：

| Section | 內容 |
|---------|------|
| **Enumerables** | **Manage Enumerables**，以及各 Enumerable 的快捷連結 |
| **Classes** | **Manage Classes**，以及各 Class 的快捷連結 |
| **Views** | **Manage Views**，以及各 Master View 的快捷連結（副標顯示目標 Class，若無則為 **No class**） |

工具列：

| 按鈕 | 何時出現 | 作用 |
|------|----------|------|
| **Generate Sample** | Enum、Class、View 皆為空 | 填入範例結構與資料 |
| **ER Diagram** | 一律可用 | 開啟實體關係圖 |

---

## 相關章節

- [快速入門](user-guide-getting-started.md)
- [範例資料說明](user-guide-sample-data.md)
- [ER Diagram](user-guide-er-diagram.md)
