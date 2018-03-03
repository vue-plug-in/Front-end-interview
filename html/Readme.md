# html

* [**`1.html5有哪些新特性、移除了那些元素`**](#html5新特性)
* [**`2.cookies，sessionStorage和localStorage 的区别`**](#存储api区别)
* [**`3.iframe有哪些缺点`**](#iframe有哪些缺点)
* [**`4.xhtml和html有什么区别`**](#xhtml和html有什么区别)
* [**`5.Canvas和SVG有什么区别`**](#canvas和svg有什么区别)
* [**`6.HTML5 为什么只需要写 <!DOCTYPE HTML>`**](#doctype)


## html5新特性
> `HTML5` 现在已经不是 `SGML` 的子集，主要是关于图像，位置，存储，多任务等功能的增加
- 1.绘画 `canvas`
- 2.用于媒介回放的 `video` 和 `audio` 元素
- 3.本地离线存储 `localStorage` 长期存储数据，浏览器关闭后数据不丢失
- 4.`sessionStorage` 的数据在浏览器关闭后自动删除
- 5.语意化更好的内容元素，比如`article`、`footer`、`header`、`nav`、`section`
- 6.表单控件，`calendar`、`date`、`time`、`email`、`url`、`search`
- 7.新的技术`webworker`, `websocket`, `Geolocation`

> 移除的元素
- 1.纯表现的元素：`basefont，big，center，font, s，strike，tt，u`
- 2.对可用性产生负面影响的元素：`frame，frameset，noframes`

## 存储api区别
- `cookie`是网站为了标示用户身份而储存在用户本地终端（`Client Side`）上的数据（通常经过加密）

- `cookie`数据始终在同源的`http`请求中携带（即使不需要），记会在浏览器和服务器间来回传递

- `sessionStorage`和`localStorage`不会自动把数据发给服务器，仅在本地保存

> 存储大小
- `cookie`数据大小不能超过4k
- `sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大

> 有期时间
- `localStorage`存储持久数据，浏览器关闭后数据不丢失除非主动删除数据
- `sessionStorage`数据在当前浏览器窗口关闭后自动删除
- `cookie`设置的`cookie`过期时间之前一直有效，即使窗口或浏览器关闭

## iframe有哪些缺点
- `iframe`会阻塞主页面的`Onload`事件
- 搜索引擎的检索程序无法解读这种页面，不利于`SEO`
- `iframe`和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载
- 使用`iframe`之前需要考虑这两个缺点。如果需要使用`iframe`，最好是通过`javascript`动态给`iframe`添加`src`属性值，这样可以绕开以上两个问题

## xhtml和html有什么区别
> 一个是功能上的差别
- 主要是`XHTML`可兼容各大浏览器、手机以及`PDA`，并且浏览器也能快速正确地编译网页

> 另外是书写习惯的差别
- `XHTML`元素必须被正确地嵌套，闭合，区分大小写，文档必须拥有根元素

## canvas和svg有什么区别
- 1.`svg`绘制出来的每一个图形的元素都是独立的`DOM`节点，能够方便的绑定事件或用来修改。`canvas`输出的是一整幅画布
- 2.`svg`输出的图形是矢量图形，后期可以修改参数来自由放大缩小，不会是真和锯齿。而`canvas`输出标量画布，就像一张图片一样，放大会失真或者锯齿

## doctype
- 1.`HTML5`不基于`SGML`，因此不需要对`DTD`进行引用，但是需要doctype来规范浏览器的行为
- 2.而`HTML4.01`基于`SGML`,所以需要对`DTD`进行引用，才能告知浏览器文档所使用的文档类型