# 页面加载速度

* [**`1.从浏览器打开到页面渲染完成花费了多少时间`**](#从浏览器打开到页面渲染完成花费了多少时间)

## 从浏览器打开到页面渲染完成花费了多少时间

> 浏览器解析->查询缓存->dns 查询->建立链接->服务器处理请求->服务器发送响应->客户端收到页面->解析 HTML->构建渲染树->开始显示内容(白屏时间)->首屏内容加载完成(首屏时间)->用户可交互(DOMContentLoaded)->加载完成(load)

> 可以通过下面的方法来获取对应阶段的耗时
```javascript
let timing = performance.timing
readyStart = timing.fetchStart - timing.navigationStart
redirectTime = timing.redirectEnd - timing.redirectStart
appcacheTime = timing.domainLookupStart - timing.fetchStart
unloadEventTime = timing.unloadEventEnd - timing.unloadEventStart
lookupDomainTime = timing.domainLookupEnd - timing.domainLookupStart
connectTime = timing.connectEnd - timing.connectStart
requestTime = timing.responseEnd - timing.requestStart
initDomTreeTime = timing.domInteractive - timing.responseEnd
domReadyTime = timing.domComplete - timing.domInteractive
loadTime = timing.loadEventEnd - timing.navigationStart
//过早获取时 domComplete有时会是0loadEventTime = timing.loadEventEnd - timing.loadEventStart;loadTime = timing.loadEventEnd - timing.navigationStart;
//过早获取时 loadEventEnd有时会是0
console.log('准备新页面时间耗时: ' + readyStart)
console.log('redirect 重定向耗时: ' + redirectTime)
console.log('Appcache 耗时: ' + appcacheTime)
console.log('unload 前文档耗时: ' + unloadEventTime)
console.log('DNS 查询耗时: ' + lookupDomainTime)
console.log('TCP连接耗时: ' + connectTime)
console.log('request请求耗时: ' + requestTime)
console.log('请求完毕至DOM加载: ' + initDomTreeTime)
console.log('解释dom树耗时: ' + domReadyTime)
console.log('从开始至load总耗时: ' + loadTime)
```

### 1.服务器部分优化
> 后端部分可以对缓存，dns查询时间，链接时间，处理请求时间，响应时间等进行优化。
- 1.dns查询时间可以使用httpdns或是dns预加载，域名收敛等手段优化。
- 2.建立连接的重点是长连接和链接复用，keep-alive，long-polling，http-straming，websocket或是自己写过别的协议，更好的是直接上http2。为了优化链接的环节，前端还需要对资源使用cdn，雪碧图，代码合并等手段。
- 3.移动端访问PC端页面需要跳转到移动端页面时，要再服务器端使用302跳转，不要在前端进行跳转。还有就是启用hsts，要求浏览器在之后的访问使用https，减少无谓的http跳转https，同时还可以防止ssl剥离攻击，提升安全性。
- 4.服务器发送响应环节，可以使用Transfer-Encoding=chunked，多次返回响应，具体操作查询bigpipe。还有就是减小cookie的体积等等。

### 2.前端部分优化要点
> 前端部分可以对白屏时间，首屏事件，可交换时间，加载完成时间进行优化。