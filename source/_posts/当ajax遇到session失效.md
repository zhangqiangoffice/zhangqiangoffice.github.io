---
title: '当ajax遇到session失效'
tags: []
date: 2016-10-10 14:37:15
---

在拦截器或过滤器中加入如下代码

在header中加入sessionstatus 

Java代码  
```java
    if (session == null || session.getAttribute("user") == null) {  
        // *用户登录以后需手动添加session  
        if("XMLHttpRequest".equals(request.getHeader("X-Requested-With"))){  
            response.setHeader("sessionstatus", "timeout");  
            response.setHeader("redirectUrl", request.getContextPath() + "/login.jsp");  
        } else {  
            response.sendRedirect(request.getContextPath() + "/login.jsp");  
        }  
        // 如果session为空表示用户没有登录就重定向到login.jsp页面  
        return;  
    }  
``` 

    页面引入jquery ajax请求的通用代码

    解析header中的sessionstatus 

    Js代码  
```js
    //全局的AJAX访问，处理AJAX清求时SESSION超时  
    if(typeof($)!="undefined"){  
        $.ajaxSetup({  
            contentType : "application/x-www-form-urlencoded;charset=utf-8",  
            complete : function(XMLHttpRequest, textStatus) {  
                // 通过XMLHttpRequest取得响应头，sessionstatus  
                var sessionstatus = XMLHttpRequest.getResponseHeader("sessionstatus");  
                if (sessionstatus == "timeout") {  
                    // 这里怎么处理在你，这里跳转的登录页面  
                    alert("登录失效，请重新登录");  
                    window.location.replace(XMLHttpRequest.getResponseHeader("redirectUrl"));  
                }  
            }  
        });  
    }  
```