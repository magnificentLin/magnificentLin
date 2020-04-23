---
title: 模块模式
author: magnificent
date: 2020-04-02 01:09:00 +0800
categories: [Blogging, Tutorial]
tags: [js设计模式]
---

### * 什么是闭包?他们两者有什么关系？

变量的作用域分为两种，全局变量和局部变量。全局变量作用域是整个程序，局部变量作用域是在所属的函数内。 闭包就是定义在函数内部的子函数，外部函数能够通过这个子函数来读取函数内部的局部变量。模块模式使用闭包来解决私有和公有的封装问题。

### 变量泛滥，命名重复问题

多个人一起开发一个项目时，定义变量的时候可能会产生命名冲突。

### 详细说明(function(){})()

(function(){})()是匿名函数，使用function关键字声明函数，但未指定函数名。前面的括号内是函数体，后面的()表示执行。用匿名函数让变量的作用域控制在匿名函数之内。

{% raw %}
```liquid
const modal = (function(){
   const _count = 0  // 私有变量
   const  m1 = function(){} // 私有方法
   return{
      m1:m1 // 公有方法
   }
})()

modal.m1()
```
{% endraw %}

通过return把内部方法m1暴露出来。外部调用modal.m1()访问私有变量_count并且可以传入参数执行内部代码。

### 模块模式的应用场景

{% raw %}
```liquid
const _this = this
const setData = (function () {
  return {
    set: function (name,mobile,avatar) {
      _this.setData({
        name: name,
        mobile: mobile,
        avatar: avatar
      })
    }
  }
})()
if (app.globalData.userCallback) {
  setData.set(app.globalData.user.nickName,app.globalData.user.mobile,app.globalData.user.avatar)
} else {
  app.globalData.userCallback = user => {
    setData.set(user.nickName,user.mobile,user.avatar)
  }
}
```
{% endraw %}
