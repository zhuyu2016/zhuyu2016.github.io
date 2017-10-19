---
layout:         post
title:          关于CSS里面优先级的问题
subtitle:       CSS priority level
card-image: 
date:           2016-5-14 9:00:19
tags:           code
post-card-type: article
---

## 计算


> !important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性

简单的计算方法（权值实际并不是按十进制，用数字表示只是说明思想，一万个class也不如一个id权值高）

- 内联样式表的权值为 1000 &nbsp; &nbsp;&nbsp;&nbsp;( style : " " )
- ID 选择器的权值为 100  &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;  ( id = " " )
- Class 类选择器的权值为 10    &nbsp;&nbsp;     ( class = " " )
- HTML 标签选择器的权值为 1&nbsp;&nbsp;( div,p... )

## 例子




```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style type="text/css">
        div.test{
            background-COLOR:#a00;
            width:100px;
            height: 100px;
        }

        .test.test2{
            background-COLOR:#0e0;
            width:100px;
            height: 100px;
        }
    </style>
</head>
<body>
    <div class="test test2"></div>
</body>
</html>
```
### 到底div是应用那条规则呢?

> div.class的权值是1+10=11，而.test1 .test2的权值是10+10=20，所以div会应用.test1 .test2变成绿色。

### 需注意的：

　　①、!important的优先级是最高的，但要谨慎使用;

　　②、优先级相同时，则采用就近原则，选择最后出现的样式;

　　③、继承得来的属性，其优先级最低;







如需博文转载，请附加原文链接

博客地址：http://www.cnblogs.com/zxjwlh
