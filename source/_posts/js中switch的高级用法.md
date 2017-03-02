---
title: 'js中switch的高级用法'
tags: []
date: 2016-10-21 11:33:53
---

项目中用到的一段switch代码：
```js
//在switch的case中使用条件判断
let label = '';
const choice = this.props.insurance.choice;
switch (true) {
    case choice === 0:
        label = "投保";
        break;
    case choice === -1:
        label = "不投保";
        break;
    case choice >= 10000:
        label = (choice / 10000) + '万'
        break;
    default:
        label = choice;
        break;
}
```