---
title: '判断JS对象是否拥有某属性'
tags: []
date: 2016-10-26 14:11:48
---

两种方式，但稍有区别

1，in 运算符

    <span class="hljs-keyword">var</span> obj = {name:<span class="hljs-string">'jack'</span>};
    alert(<span class="hljs-string">'name'</span> <span class="hljs-keyword">in</span> obj); <span class="hljs-comment">// --&gt; true</span>
    alert(<span class="hljs-string">'toString'</span> <span class="hljs-keyword">in</span> obj); <span class="hljs-comment">// --&gt; true</span>`</pre>

    可看到无论是name，还是原形链上的toString，都能检测到返回true。

    2，hasOwnProperty 方法

    <pre class="prettyprint">`<span class="hljs-keyword">var</span> obj = {name:<span class="hljs-string">'jack'</span>};
    obj.hasOwnProperty(<span class="hljs-string">'name'</span>); <span class="hljs-comment">// --&gt; true</span>
    obj.hasOwnProperty(<span class="hljs-string">'toString'</span>); <span class="hljs-comment">// --&gt; false</span>

原型链上继承过来的属性无法通过hasOwnProperty检测到，返回false。

需注意的是，虽然in能检测到原型链的属性，但for in通常却不行。