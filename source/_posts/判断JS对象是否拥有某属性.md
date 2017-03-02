---
title: '判断JS对象是否拥有某属性'
tags: []
date: 2016-10-26 14:11:48
---

两种方式，但稍有区别

1，in 运算符

```js
  var obj = {name:'jack'};
  alert('name' in obj); // --&gt; true
  alert('toString' in obj); // --&gt; true
```

    可看到无论是name，还是原形链上的toString，都能检测到返回true。

    2，hasOwnProperty 方法

```js
  var obj = {name:'jack'};
  obj.hasOwnProperty('name'); // --&gt; true
  obj.hasOwnProperty('toString'); // --&gt; false
```

原型链上继承过来的属性无法通过hasOwnProperty检测到，返回false。

需注意的是，虽然in能检测到原型链的属性，但for in通常却不行。