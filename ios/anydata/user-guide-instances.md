# Instances

← 返回 [使用手冊目錄](user-guide.md)

**Instance** 是某個 **Class** 的一筆實際資料。結構由該 Class 的 **Properties** 決定；內容在 Instance 編輯畫面中填寫。

---

## 開啟 Instance 列表

1. 進入 Workspace → 點某個 Class（或經 **Manage Classes**）。
2. 在 Class Hub 點 **Instances (N)**。

列表導覽標題為 Class 名稱。每一列顯示：

- 標題：優先使用第一個有值的 **String** 屬性；若沒有，則為 `{ClassName} {短 ID}`
- 副標：短 ID

---

## 新增 Instance

點工具列 **Add Instance**。新列會建立並可立即編輯各屬性。

---

## 編輯 Instance

點某一列進入編輯畫面。導覽標題同列表標題規則。

每個 Property 為一個 Section，依類型使用不同控制項：

| 類型 | 操作 |
|------|------|
| **String** / **Integer** / **Float** | 文字欄；placeholder 為 **Optional** |
| **Date/Time** / **Date** / **Time** | DatePicker；可用 **Clear**，以及 **Set to now** 或 **Set to today** |
| **Color** | Color picker 與色點預覽；**Clear** 可清空；無值時可能顯示 **None** |
| **Enumerable** | Picker，標籤 **Value**；可選 **None** 或某個 Value |
| **Class** | Picker，標籤 **Value**；可選 **None** 或目標 Class 的某個 Instance |

所有欄位皆可留空。

### 尚無 Properties 時

若 Class 還沒有任何屬性，編輯畫面會顯示空狀態：

- 標題概念：**No Properties**
- 說明：**Add properties to this class in Schema.**

請先到 **Properties** 建立欄位再回來編輯。

---

## 刪除 Instance

在 Instance 列表以滑動手勢刪除該列。

---

## 在哪裡編輯？

| 畫面 | 可否編輯 Instance |
|------|-------------------|
| Class → **Instances** → 編輯器 | 可以（主要入口） |
| Master View 列表 | 用於瀏覽與鑽取，不是主編輯入口 |
| Detail View 執行畫面 | **唯讀**；請回到 Class 的 Instances 編輯 |

---

## 實用提示

- Instance 列表標題依賴 String 屬性：建議為常用 Class 放一個靠前的 **Name** / **Title** 類 String 欄。
- 變更 Schema（類型或綁定）會清空該屬性既有值；大量資料時請先規劃好類型再錄入。
- 關聯欄（**Class** 類型）需先有目標 Class 的 Instances，才能在 Picker 中選到。

---

## 相關章節

- [Classes 與 Properties](user-guide-classes.md)
- [Views](user-guide-views.md)
- [範例資料說明](user-guide-sample-data.md)
