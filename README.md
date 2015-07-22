## ajax请求的一些研究

> ajax对很多人来说并不陌生，但是与后台的数据通信仍然会面临一些问题，比如跨域问题、编码问题、接口问题，这些问题似懂非懂的困扰着我们，关键是因为涉及到一些后端的知识和配合，如果不能真的明白后端做了哪些操作，我们很难在遇到问题的时候给出别人包括后端开发行之有效的解决办法，nodejs是让我们理解后端实践的一个很有利的东西！

我们联想到数据通信会想到form表单，可以往后台提交数据，保存用户数据，那么他们的做法，多数是采用刷新页面页面的方式来提交数据，这种方式是早起最常见的一种数据通信方式，他有以下几个缺点：

1、对于一些网速较慢的用户 浪费了额外的网速去重复加载内容
2、当页面请求过慢的时候 页面是处于一种“假死”状态，此时点击页面中的任何内容、图片、链接均是失效的

要想理解ajax请求，首先要了解一些ajax的基础知识，ajax其实没有特别深奥，只是涉及到几个小小的知识点

>**Ajax最大的用处是可以更新网页的部分内容而不需要刷新整个页面。**

1、创建XHR对象（**XMLHttpRequest**对象的缩写，以下统一称呼XHR）

Firefox、chrome等浏览器 均是使用 window.XMLHttpRequestl来创建XHR对象
IE是采用ActiveXObject的方式来创建XHR对象

2、


#### 同域ajax请求
你好我也好 我们大家都很好，相安无事

#### 跨域ajax请求
>**同源策略：所谓同源是指，域名，协议，端口相同。不同源的客户端脚本(javascript、ActionScript)在没明确授权的情况下，不能读写对方的资源。**

Access-Control-Allow-Origin: *.Httpsecure.org  定义了双向通信通道 允许其他域的内容可以请求
Access-Control-Allow-Credentials: true 允许经过身份验证的资源进行通信

withCredentials是XHR2 新增的一个属性，一般可以用做特性检测上，用于区分IE和高级浏览器的区别

IE下目前解决跨域问题，采用的是windowName的方式，实现的原理，围绕着一句话：

window.name 的美妙之处：name 值在不同的页面（甚至不同域名）加载后依旧存在，并且可以支持非常长的 name 值（2MB）。name 在浏览器环境中是一个全局/window对象的属性，且当在 frame 中加载新页面时，name 的属性值依旧保持不变

参考链接如下：http://www.2cto.com/Article/201504/395206.html
