---
title: 'JavaScript ES6中的var、let、const'
tags: []
date: 2016-10-12 22:34:57
---

# JavaScript ES6中的var、let、const

const 常量 

let 变量，块作用域，不能重复声明覆盖 

var 变量，函数作用域，能重复声明覆盖

*   var：声明全局变量，换句话理解就是，声明在for循环中的变量，跳出for循环同样可以使用。

```js
for(var i=0;i<=1000;i++){
    var sum=0;
    sum+=i;
}
    alert(sum);
```

    声明在for循环内部的sum，跳出for循环一样可以使用，不会报错正常弹出结果

*   let：声明块级变量，即局部变量。    
    在上面的例子中，跳出for循环，再使用sum变量就会报错
```js
'use strict';

(function() {
  var varTest = 'test var OK.';
  let letTest = 'test let OK.';

  {
    var varTest = 'varTest changed.';
    let letTest = 'letTest changed.';
  }

  console.log(varTest); //输出"varTest changed."，内部"{}"中声明的varTest变量覆盖外部的letTest声明
  console.log(letTest); //输出"test let OK."，内部"{}"中声明的letTest和外部的letTest不是同一个变量
}());
```
    

    注意：必须声明'use strict';后才能使用let声明变量否则浏览并不能显示结果

*   const：用于声明常量，也具有块级作用域
    const PI=3.14;