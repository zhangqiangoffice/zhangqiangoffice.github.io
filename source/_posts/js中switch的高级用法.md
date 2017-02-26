---
title: 'js中switch的高级用法'
tags: []
date: 2016-10-21 11:33:53
---

项目中用到的一段switch代码：

    <span class="hljs-comment">//在switch的case中使用条件判断</span>
    <span class="hljs-keyword">let</span> label = <span class="hljs-string">''</span>;
    <span class="hljs-keyword">const</span> choice = <span class="hljs-keyword">this</span>.props.insurance.choice;
    <span class="hljs-keyword">switch</span> (<span class="hljs-literal">true</span>) {
        <span class="hljs-keyword">case</span> choice === <span class="hljs-number">0</span>:
            label = <span class="hljs-string">"投保"</span>;
            <span class="hljs-keyword">break</span>;
        <span class="hljs-keyword">case</span> choice === -<span class="hljs-number">1</span>:
            label = <span class="hljs-string">"不投保"</span>;
            <span class="hljs-keyword">break</span>;
        <span class="hljs-keyword">case</span> choice &gt;= <span class="hljs-number">10000</span>:
            label = (choice / <span class="hljs-number">10000</span>) + <span class="hljs-string">'万'</span>
            <span class="hljs-keyword">break</span>;
        <span class="hljs-keyword">default</span>:
            label = choice;
            <span class="hljs-keyword">break</span>;
    }