---
title: Javascript 字串夾入變數
---

javascript 原來可在字串夾入變數, 只要用反單引號表示字串即可. (`)

```javascript
function anchor(href,text) 
{
	return `<a href="${href}">${text}</a>`;
}
```

這就不用一堆瑣碎小字串和加號連接, 更別說單雙引號交替使用的麻煩.
