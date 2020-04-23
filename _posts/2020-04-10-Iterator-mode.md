---
title: 迭代器模式
author: magnificent
date: 2020-04-10 12:22:00 +0800
categories: [js, Design Mode]
tags: [js设计模式, 迭代器模式]
---

## 什么是迭代器模式？

>迭代器就是按顺序访问一个对象内的各个元素，然后不暴露该元素的内部。
 js中经常使用的forEach遍历数组就是迭代器模式，为可以遍历不同数组提供了一种方法。从而可以用同一种方法在不同数组上进行操作。
 
 迭代器模式分为：
 * 内部迭代器（jquery中的$.each/for...of）
 * 外部迭代器（es6中的yield）

### 内部迭代器

>内部迭代器是内部定义好规则，外部只需初始调用。

```shell
 $(selector).each(function(index,element))。
```

>为每个匹配的元素规定index位置，和当前的元素的函数。

```shell
$.each(['unComplete', 'unActivation', 'activation'], function(index, value) {
   console.log([index, value]);
});

// 输出：[0, unComplete]  [1, unActivation]  [2, activation]
```

迭代器规则规定了index位置和元素。无法更改。

### 外部迭代器

```shell
    function generatorEach(type) {
      for (let [index, value] of type.entries()) {
        yield console.log([index, value]);
      }
    }

    let each = generatorEach(['unComplete', 'unActivation', 'activation']);
    each.next();
    each.next();
    each.next();

// 输出：[0, 'unComplete']  [1, 'unActivation']  [2, 'activation']
```

---

迭代器可以通过break来跳出循环。

```shell
for (let i = 0, len = list.length; i < len; i++) {
    result = callback.call(list[i], i, list[i])
    if (result === false) {
      break
    }
  }
}

each(['unComplete','unActivation','activation'], function(i, item) {
  if (item  === 'unComplete') {
    return false
  }
  console.log(item)
})
```
