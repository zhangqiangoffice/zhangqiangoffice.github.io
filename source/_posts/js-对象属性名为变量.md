---
title: 'js 对象属性名为变量'
tags: []
date: 2016-11-02 12:21:55
---

在React项目中不可避免要用到setState(obj)这个函数，其中，obj为一个对象。如果传不同的obj可以，修改组件不同的状态。有的时候就想obj能根据参数动态生成。

    handleChange(event, type) {
        <span class="hljs-keyword">let</span> val = event.target.value.trim();
        <span class="hljs-keyword">this</span>.setState({
            type: val 
        });
    }`</pre>

    这里就是希望通过参数type来修改不同的状态，但这么写是不能正确实现的，因为type是一个变量，这里是要用变量作为js对象的属性名，正确写法如下：

    <pre class="prettyprint">`handleChange(event, type) {
        <span class="hljs-keyword">let</span> val = event.target.value.trim();
        <span class="hljs-keyword">let</span> change = {};
        change[type] = val;
        <span class="hljs-keyword">this</span>.setState(change);
    }