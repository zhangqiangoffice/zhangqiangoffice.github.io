---
title: '人生第一段gulp代码'
tags: [gulp]
date: 2016-10-11 16:08:48
---

# 人生第一段gulp代码

学习新技术一定要有用处，只有不断使用，真正投入实战，新技术才会不断被磨炼，才能真正被掌握。

公司的电脑加装了一块显示屏，为了充分利用两块屏幕，我想到要实现自动刷新浏览器的功能。这样我就能在写CSS代码的时候不离开键盘去刷新浏览器来查看页面效果了。

听说gulp的功能强大，我一直想学，正好借此机会，研究一下gulp，其实也不是很难，以下就是gulp监听CSS文件变动，并刷新浏览器的代码，这也是我人生第一段gulp代码：

    <span class="hljs-comment">//安装node、gulp、browser-sync的过程就不赘述了 </span>
    <span class="hljs-keyword">var</span> gulp = <span class="hljs-built_in">require</span>(<span class="hljs-string">'gulp'</span>);
    <span class="hljs-keyword">var</span> BrowserSync = <span class="hljs-built_in">require</span>(<span class="hljs-string">'browser-sync'</span>).create();

    gulp.task(<span class="hljs-string">'browser-sync'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
        <span class="hljs-comment">//因为已经用Tomcat启动了服务器，所以这里用了代理服务，这也是难点</span>
        BrowserSync.init({
            proxy: <span class="hljs-string">'http://localhost:8080/ms-console/'</span>
        });
    });

    gulp.task(<span class="hljs-string">'watch'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">()</span> {</span>
        <span class="hljs-comment">//监听Tomcat下的CSS文件，若有变动就重新加载BrowserSync</span>
        gulp.watch(<span class="hljs-string">'D:/apache-tomcat-7.0.53/apache-tomcat-7.0.53/webapps/ms-console/static/css/statement/lines_month.css'</span>).on(<span class="hljs-string">'change'</span>,BrowserSync.reload);
    });

    <span class="hljs-comment">//定义gulp任务</span>
    gulp.task(<span class="hljs-string">'default'</span>, [<span class="hljs-string">'browser-sync'</span>, <span class="hljs-string">'watch'</span>]);