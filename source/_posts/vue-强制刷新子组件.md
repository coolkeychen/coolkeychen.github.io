---
title: vue 强制刷新子组件
date: 2020-07-07 11:29:38
tags:
---
## 引言
>把一个组件重置到初始状态是一个常见的需求，推荐的做法有两种，一种是父组件重置子组件的 prop，另一种是子组件暴露一个重置的方法供父组件调用。但有些时候，子组件既没有提供重置的方法，也没提供 prop 来重置自己的状态。更重要的是，这个子组件我们还动不了。于是我们就需要一种 hack 的方式来强制子组件重置到初始状态

```
// 原理就是：采用v-if会销毁组件并且重绘，这样就会重载组件
  <Son v-if="isReader == true" ref="IncomeStatisticsChild"></Son>

  this.isReader = false;

// 然后你的方法成功后
// Vue 实现响应式并不是数据发生变化之后 DOM 立即变化，而是按一定的策略进行 DOM 的更新。
// 在vue的深入响应式原理中有解释：
// $nextTick 是在下次 DOM 更新循环结束之后执行延迟回调，在修改数据之后使用 $nextTick，则可以在回调中获取更新DOM

  this.$nextTick(() => {
    this.isReader = true;
  });
```