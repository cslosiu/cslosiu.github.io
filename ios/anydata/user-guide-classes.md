# Classes 與 Properties

← 返回 [使用手冊目錄](user-guide.md)

**Class** 定義一類資料的結構（類似資料表）。每個 Class 可有多個 **Properties**（欄位），以及多筆 **Instances**（資料列）。

所有 Property 皆為選填（optional），目前沒有「必填」設定。

---

## 開啟 Classes

在 Workspace 首頁點 **Manage Classes**，畫面標題為 **Classes**。

每一列副標格式大致為：**`{N} properties · {M} instances`**。

也可從首頁直接點某個 Class 名稱，進入該 Class 的 **Class Hub**。

---

## 新增 Class

1. 在 **Classes** 點 **Add**。
2. 在 **New Class** 對話框輸入名稱後 **Create**。

---

## Class Hub

進入某個 Class 後，常見操作：

| 項目 | 說明 |
|------|------|
| **Rename Class** | 重新命名此 Class |
| **Properties** | 進入 Schema，管理屬性 |
| **Instances (N)** | 進入該 Class 的資料列表（N 為筆數） |

---

## 管理 Properties（Schema）

在 Class Hub 點 **Properties**，畫面標題為 **Properties**。

### 新增 Property

1. 點 **Add Property**。
2. 在 **New Property** 表單填寫：
   - **Property name** — 欄位名稱
   - **Type** — 屬性類型（見下表）
   - 若類型為 **Enumerable**：再選綁定的 **Enumerable**
   - 若類型為 **Class**：再選目標 **Class**（此欄將指向該 Class 的某一 Instance）
3. 點 **Add**（或 **Cancel**）。

### 編輯 / 排序 / 刪除

- 可調整屬性名稱、類型與綁定對象。
- 可重新排序 Properties。
- 可刪除 Property（相關 Instance 上的該欄值一併移除）。

> **重要：** 變更 Property 的類型，或變更其綁定的 Enumerable / Class，會清除該屬性在所有 Instances 上的既有值。

---

## 屬性類型一覽

| 介面顯示名稱（Type） | 用途 | Instance 編輯方式 |
|----------------------|------|-------------------|
| **String** | 文字 | 文字欄（placeholder：**Optional**） |
| **Date/Time** | 日期＋時間 | 日期時間選擇器；**Set to now** / **Clear** |
| **Date** | 僅日期 | 日期選擇器；**Set to today** / **Clear** |
| **Time** | 僅時間 | 時間選擇器；**Set to now** / **Clear** |
| **Integer** | 整數 | 數字鍵盤輸入 |
| **Float** | 小數 | 小數鍵盤輸入 |
| **Color** | 顏色 | 系統 Color picker；可 **Clear** |
| **Enumerable** | 綁定 Enumerable 的選項 | Picker；可選 **None** |
| **Class** | 指向另一 Class 的 Instance | Picker；可選 **None** |

列表或唯讀畫面中，空值通常顯示為 **—**。

列表摘要可能顯示為：

- `Enumerable · {名稱}`
- `Class · {名稱}`
- 或其他類型的 display name

---

## Class 參照（關聯）

當屬性類型為 **Class** 時：

1. 建立時必須指定目標 Class（例如 Task 的 **Project** 屬性指向 Project）。
2. 編輯 Instance 時，從目標 Class 的現有 Instances 中選擇一筆，或選 **None**。
3. 這類屬性是建立 **Detail View** 的前提：Detail 會找「其他 Class 上、指向 Master 所選 Class」的 Class 類型屬性作為連結。

跨 Workspace 的參照目前不支援。

---

## 刪除 Class

在 **Classes** 列表刪除該 Class。其所屬 Properties 與 Instances 一併移除。

若其他 Class 有屬性以 **Class** 類型指向此 Class，刪除前請先檢查關聯是否仍需要。

---

## 建議建模順序

1. 先建立被參照的 Class（例如 Person、Company）。
2. 再建立會指向它們的 Class（例如 Project、Task）。
3. 需要固定選項時，先建 Enumerable，再建屬性綁定它。
4. 結構穩定後再大量錄入 Instances，並建立 Views。

---

## 相關章節

- [Enumerables](user-guide-enumerables.md)
- [Instances](user-guide-instances.md)
- [Views](user-guide-views.md)
- [ER Diagram](user-guide-er-diagram.md)
