---
title: '关于For of'
tags: []
date: 2016-11-16 15:40:00
---

For of 是ES6的语法，所以有很多浏览器不支持，比如Android的WebView控件，这一点很容易想到。但是我在写React组件时，通过Balble进行了ES6到ES5转化，结果在涉及到For of时，程序不能正常运行，AS里的报错是Symbol is not defined。后来将for of替换成其他方式，问题就解决了。