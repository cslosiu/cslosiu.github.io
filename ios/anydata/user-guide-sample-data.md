# 範例資料說明（Generate Sample）

← 返回 [使用手冊目錄](user-guide.md)

當 Workspace 內 **沒有任何** Enumerable、Class、View、Form 時，工具列會出現 **Generate Sample**。點一下即可建立一套以 Oracle **HR** sample schema 為靈感的示範資料，方便立刻體驗 Classes、Forms、多 Class JOIN Views 與關聯。

> 若已手動建立過任何 Enum / Class / View / Form，按鈕不會出現。需要範例時請開一個全新的空 Workspace。

以下名稱皆與 App 內實際內容一致（英文）。

---

## Classes（HR tables）

| Class | Properties（名稱 · 類型／綁定） |
|-------|--------------------------------|
| **Region** | Name (String) |
| **Country** | Name (String), Code (String), Region (Class → Region) |
| **Location** | City (String), Street Address (String), Postal Code (String), State Province (String), Country (Class → Country) |
| **Job** | Title (String), Job Code (String), Min Salary (Float), Max Salary (Float) |
| **Department** | Name (String), Location (Class → Location), Manager (Class → Employee) |
| **Employee** | Name (String), Email (String), Phone Number (String), Hire Date (Date), Job (Class → Job), Salary (Float), Commission Pct (Float), Manager (Class → Employee), Department (Class → Department) |
| **Job History** | Employee (Class → Employee), Start Date (Date), End Date (Date), Job (Class → Job), Department (Class → Department) |

關聯大致為：`Region` → `Country` → `Location` → `Department` ← `Employee` → `Job`，以及 `Employee` 自引用 Manager、`Job History` 記錄過往職務。

---

## 樣本資料規模（約）

| Class | 約略內容 |
|-------|----------|
| **Region** | Europe, Americas, Asia, Middle East and Africa |
| **Country** | US, UK, CA, DE, JP |
| **Location** | Southlake、Seattle、Toronto、London、Oxford 等 |
| **Job** | AD_PRES、AD_VP、IT_PROG、SA_MAN、SA_REP、PU_*、MK_*、HR_REP、AC_* 等 |
| **Department** | Executive、IT、Finance、Sales、Marketing 等 |
| **Employee** | Steven King 組織樹（含 IT／Sales／Finance 等，取自經典 HR 姓名） |
| **Job History** | 數筆過往職務紀錄 |

實際欄位值以 App 產生結果為準。

---

## 預建 Views

| View | 說明 |
|------|------|
| **Employees** | 全部 Employee 欄位 |
| **Departments** | 全部 Department 欄位 |
| **Jobs** | 全部 Job 欄位 |
| **Locations** | Location JOIN Country（城市、地址、國家） |
| **Employee Directory** | Employee JOIN Department + Job；篩選 Salary >= 10000 |
| **Salary by Department** | Employee JOIN Department；依部門 GROUP BY，含 Count / Avg / Sum(Salary) |
| **Job History** | 全部 Job History 欄位（Class 欄可 drill） |
| **Org Chart** | Employee 精簡欄（Name、Job、Manager、Department、Salary） |

---

## 預建 Forms

每個 Class 各有一個同名 Form（Region、Country、Location、Job、Department、Employee、Job History），可直接用來新增資料。

---

## 建議體驗路徑

1. 開啟 **Employee Directory** 看多 Class JOIN 與高薪篩選。
2. 開啟 **Salary by Department** 看 GROUP BY 與聚合。
3. 開啟 **Org Chart**，點 Manager / Department 做 Class drill-down。
4. 用 **Employee** Form 新增一筆員工。
5. 回到 Workspace 點 **ER Diagram** 檢視整體關係。

---

## 相關章節

- [快速入門](user-guide-getting-started.md)
- [Views](user-guide-views.md)
- [ER Diagram](user-guide-er-diagram.md)
