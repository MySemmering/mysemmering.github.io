# 概念
强缓存和协商缓存是浏览器对网页资源的一种缓存机制。
强缓存主要依赖Cache-Control和Expires这两个字段
### 强缓存

Cache-control：http1.1的产物

**public：**服务器和客户端都缓存<br/>
**provate：**只有客户端缓存<br/>
**max-age：**缓存有效期，单位秒<br/>
**no-cache：**表示不使用强缓存，而是用协商缓存来判断缓存。客户端缓存内容是否使用缓存则需要经过协商缓存来验证决定。表示不使用 Cache-Control的缓存控制方式做前置验证，而是使用 Etag 或者Last-Modified字段来控制缓存。需要注意的是，no-cache这个名字有一点误导。设置了no-cache之后，并不是说浏览器就不再缓存数据，只是浏览器在使用缓存数据时，需要先确认一下数据是否还跟服务器保持一致。<br/>
**no-store：**禁用缓存。所有内容都不会被缓存，即不使用强制缓存，也不使用协商缓存<br/>

Expires：http1.0的产物

expires用于指定资源过期时间，expires的一个最大缺陷就是时间读取的是本地时间，如果本地时间做了修改，会影响缓存的判断，可能会导致缓存失效。这也是cache-control引入max-age的原因之一。

### 协商缓存
### 启发式缓存
它的计算方式为根据响应头中2个时间字段 Date 和 Last-Modified 之间的时间差值,取其值的10%作为缓存时间周期