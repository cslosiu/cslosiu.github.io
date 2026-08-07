# ER Diagram

← 返回 [使用手冊目錄](user-guide.md)

**ER Diagram**（實體關係圖）以視覺化方式呈現目前 Workspace 中的 **Classes**、**Enumerables** 及其關聯，方便檢查資料模型。

---

## 開啟

在 Workspace 首頁工具列點 **ER Diagram**，以全螢幕方式開啟。標題為 **ER Diagram**。點 **Done** 關閉。

---

## 空狀態

若尚無 Class 也無 Enumerable，會顯示：

- **No Entities**
- **Add classes or enumerables to see an entity-relation diagram.**

---

## 圖上元素

| 元素 | 說明 |
|------|------|
| 標有 **Class** 的方塊 | 一個 Class 及其 Properties；無屬性時可能顯示 **(no properties)** |
| 標有 **Enum** 的方塊 | 一個 Enumerable |
| 連線 | Class 之間或與 Enumerable 的關係 |
| 圖例 | **Class** · **Enumerable** · **Crow's foot = child · Bar = parent** |

顏色屬性在圖上可能以色點表示；無障礙標示可能包含 **No color** / **Color swatch**。

---

## 操作

| 操作 | 說明 |
|------|------|
| 捏合縮放 | Pinch to zoom |
| 拖曳表格 | 移動個別實體方塊 |
| 拖曳背景 | 平移整張圖 |
| **Zoom out** / **Zoom in** | 底部縮放控制 |
| **Recenter** | 重新置中 |
| **Reset** | 重設版面／縮放 |

在較小螢幕上可能看到提示：

> **Pinch to zoom · Drag tables · Drag background to pan**

---

## 匯出

點 **Export**，可選：

- **Export PNG**
- **Export PDF**

成功後會透過系統分享表單送出；檔名大致為 `{workspace名稱}-ER.png` 或 `{workspace名稱}-ER.pdf`。

若失敗，可能出現 **Export Failed**，以及 **Could not render PNG.** 或 **Could not render PDF.**

> 目前 App **僅支援**匯出 ER 圖（PNG/PDF），不支援把 Instances 或整個 Workspace 匯出為一般資料檔。

---

## 使用時機

- 幫自己或他人理解「哪個 Class 指向哪個 Class」
- 建立 Master / Detail 前，確認有沒有可用的 class-reference 連結
- 對外說明資料結構時，匯出 PNG/PDF 分享

---

## 相關章節

- [Classes 與 Properties](user-guide-classes.md)
- [Views](user-guide-views.md)
