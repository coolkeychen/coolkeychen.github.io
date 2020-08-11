---
title: vue复制并选中
date: 2020-04-28 17:52:37
tags: vue
---

## 前言
> 最近做了几个活动专题页，经常用到复制推荐语，并且模拟选中状态功能并分享到朋友圈的功能，需要用到原生的复制功能，以下是复制功能以及模拟选中的状态

1. 复制功能
```
  let url = this.recommendText;
  let oInput = document.createElement('input');
  oInput.value = url;
  document.body.appendChild(oInput);
  oInput.select(); // 选择对象;
  document.execCommand("Copy"); 
  oInput.remove();
```

2. 模似选中状态功能
```
  const range = document.createRange();
  range.selectNode(document.getElementById('copytext'));
  const selection = window.getSelection();
  if(selection.rangeCount > 0) selection.removeAllRanges();
  selection.addRange(range);
```