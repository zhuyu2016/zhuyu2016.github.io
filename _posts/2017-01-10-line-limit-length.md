---
layout:         post
title:          Web限制字符长度
subtitle:       line-limit-length
card-image:     https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1508415843019&di=f8e37a6bbc8502c33f84b1ae87cf28e1&imgtype=0&src=http%3A%2F%2Fwww.cdxwcx.com%2Fupload%2Fimage%2F20141120%2F201411201720148608691.png
date:           2017-01-10 2:24:10
tags:           code
post-card-type: image
---


> 为了保证页面的整洁美观，在很多的时候，我们常需要隐藏超出长度的文字。这在列表条目，题目，名称等地方常用到。

### 1. 文字超出一行，省略超出部分，显示'...' 
   如果这种情况比较多，可以取一个切合作用的类名用于复用。
```css
.line-limit-length {
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap; //文本不换行，这样超出一行的部分被截取，显示...
}
```

```html
<div class="item">
<p class="line-limit-length">最新消息：神秘地球黑洞深不可测，不停吸入周围海水。</p>
<i class="icon icon-arrow-Go"></i> //图标字体
</div>
```

![](http://img.blog.csdn.net/20160309193259989)

***
### 2. 然后给定容器宽度限制，超出部分省略

```css
.product-buyer-name {
max-width: 110px;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
```

```html
<h5 class="product-buyer-name">橘子橘子</h5>
<h5 class="product-buyer-name">橘子橘子匿名用户匿名</h5>
```
![](http://img.blog.csdn.net/20160309192609690)
![](http://img.blog.csdn.net/20160309192832691)
***
