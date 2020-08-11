---
title: css3 word-break 属性无效问题
date: 2020-08-11 15:16:20
tags: 
  - css3
---

> 今天在整理 blog，看到以往的blog 样式有点丑，代码区块不会自动换行，一条又一条又粗又灰的滚动条，影响到整个页面的美观。看了一下代码区块的样式，word-break 没生效，导致无法自动换行

## 为什么 word-break 没生效 ？
1. word-break 不支持行内元素，span
2. 一般情况下，元素拥有默认的white-space:normal（自动换行，不换行是white-space:nowrap），可能是元素中设置的white-space是norwrap导致，无法换行。所以需要
```
white-space:normal;
word-break:break-all;
```

## 总结
问题解决了， 感觉自己对 css3 掌握得还不是那么熟练，还需要对这一块加强练习
