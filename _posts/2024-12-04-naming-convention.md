---
title: 數據庫物件命名慣例
---

老話題了，但以下文章震撼了我。

https://stackoverflow.com/questions/4702728/relational-table-naming-convention/4703155#4703155

最有趣的是外鍵使用謂語的句法，比如 Customer_Initiates_SalesOrder_fk，連結 Cutomer 表和 SalesOrder 表，顯然這是 1-N 的關係。那麼他規定 master 表在前, child 表在後。
