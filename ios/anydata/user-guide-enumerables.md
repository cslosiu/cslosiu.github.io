# Enumerables

← 返回 [使用手冊目錄](user-guide.md)

**Enumerable** 用來定義一組固定可選值（Values），例如狀態或角色。建立 Class 屬性時，若類型選 **Enumerable**，即可綁定某個 Enumerable，讓 Instance 以選擇方式填值。

---

## 開啟列表

在 Workspace 首頁：

- 點 **Manage Enumerables**，或
- 直接點某個已存在的 Enumerable 名稱。

**Manage Enumerables** 畫面標題為 **Enumerables**。每一列顯示名稱與 **`{N} values`**。

---

## 新增 Enumerable

1. 點 **Add**。
2. 在 **New Enumerable** 對話框輸入 **Name**。
3. 點 **Create**（或 **Cancel**）。

接著進入該 Enumerable 的編輯畫面。

---

## 編輯 Enumerable

編輯畫面包含：

| Section | 說明 |
|---------|------|
| **Name** | Enumerable 名稱（placeholder：**Enumerable name**） |
| **Values** | 可選值列表 |

### 新增 Value

1. 點 **Add Value**。
2. 在 **New Value** 對話框的 **Value** 欄位輸入名稱。
3. 點確認建立。

### 重新命名 Value

向左滑該值 → **Rename** → 在 **Rename Value** 中修改後儲存。

### 刪除 Value

向左滑該值 → **Delete**。

### 調整順序

使用 **Edit** 進入編輯模式後，以拖曳把手重新排序 Values。

### 重複值

同一 Enumerable 內，Value 名稱在去除前後空白後必須唯一（比對區分大小寫）。若重複，會出現 **Duplicate Value** 警示，訊息為 `"…" already exists.`，點 **OK** 關閉。

---

## 刪除 Enumerable

在 **Enumerables** 列表刪除該列即可。

> 若已有 Property 綁定此 Enumerable，刪除前請先確認是否仍需要該選項。變更屬性綁定可能影響既有 Instance 值。

---

## 使用時機建議

- 狀態欄（例如 To Do / In Progress / Done）→ 建 Enumerable，屬性類型選 **Enumerable**
- 需要自由輸入的文字 → 用 **String**，不必建 Enumerable
- 需要指向另一筆紀錄（例如負責人）→ 用 **Class** 類型屬性，而非 Enumerable

---

## 相關章節

- [Classes 與 Properties](user-guide-classes.md)
- [Instances](user-guide-instances.md)
- [範例資料說明](user-guide-sample-data.md)
