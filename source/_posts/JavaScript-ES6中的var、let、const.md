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

    <span class="hljs-keyword">for</span>(<span class="hljs-keyword">var</span> i=<span class="hljs-number">0</span>;i&lt;=<span class="hljs-number">1000</span>;i++){
        <span class="hljs-keyword">var</span> sum=<span class="hljs-number">0</span>;
        sum+=i;
    }
        alert(sum);`</pre>

    <pre>`声明在for循环内部的sum，跳出for循环一样可以使用，不会报错正常弹出结果
    `</pre>

*   let：声明块级变量，即局部变量。    在上面的例子中，跳出for循环，再使用sum变量就会报错

    <pre class="prettyprint">`<span class="hljs-pi">'use strict'</span>;

    (<span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
      <span class="hljs-keyword">var</span> varTest = <span class="hljs-string">'test var OK.'</span>;
      <span class="hljs-keyword">let</span> letTest = <span class="hljs-string">'test let OK.'</span>;

      {
        <span class="hljs-keyword">var</span> varTest = <span class="hljs-string">'varTest changed.'</span>;
        <span class="hljs-keyword">let</span> letTest = <span class="hljs-string">'letTest changed.'</span>;
      }

      console.log(varTest); <span class="hljs-comment">//输出"varTest changed."，内部"{}"中声明的varTest变量覆盖外部的letTest声明</span>
      console.log(letTest); <span class="hljs-comment">//输出"test let OK."，内部"{}"中声明的letTest和外部的letTest不是同一个变量</span>
    }());`</pre>

    <pre>`注意：必须声明'use strict';后才能使用let声明变量否则浏览并不能显示结果

*   const：用于声明常量，也具有块级作用域
    const PI=3.14;