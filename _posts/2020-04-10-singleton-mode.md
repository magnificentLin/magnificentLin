---
title: 单例模式
author: magnificent
date: 2020-04-10 12:22:00 +0800
categories: [js, Design Mode]
tags: [js设计模式, 单例模式]
---

## 什么是单例模式？

>保证一个类只有一个实例。用户可以通过一个全局接口访问该实例。简单来说，同种类型的只能被创建一次。如果实例已经有了，就返回该实例，如果没有，就创建一个实例。

## 单例模式的应用场景

```shell
this.basicList = {
  timeType: value.timeType,
  number: parseInt(value.number),
  standardPrice: parseInt(value.standardPrice),
  salePrice: parseInt(value.salePrice),
  ticketType: value.ticketType
}
```

```shell
const changeParams = {
  params: {},
  id: undefined
},
```
