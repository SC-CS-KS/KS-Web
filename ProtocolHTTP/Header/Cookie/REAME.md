# Cookie

## 背景

HTTP协议本身是一种简单的，无连接，无状态的协议。
但互联网很多应用场景需要记住状态来提升用户体验，
比如登录，我们希望登录一次就可以在全站访问，而不是每次访问都要用户输入一次用户名密码。

 为了解决这个问题，网景公司发明了Cookie，
 并把Cookie定义为HTTP Header的一个字段，要求浏览器在同源的情况下，自动带上Cookie信息，
 这样服务端可以从Cookie来判断这个用户的上下文信息，比如用户登录态。

## 标准

采用key=value的形式表示。

### 属性

* 定义了五个属性
```text
控制作用范围的domain和path
制作用时间的expire或者MaxAge
控制安全性的HTTPOnly和Secure
```

### SameSite

*  背景
Web前端安全，OWASP排名前两位的安全漏洞就是XSS和CSRF，其基本原理都是攻破了浏览器同源策略的限制。
处理CSRF漏洞目前的措施一般是验证referer或者是使用安全token。

而google则希望从标准层面去根治这个排名第二的前端安全漏洞。
其方案就是给Cookie新增一个属性，用这个属性来控制什么情况下可以发送Cookie，这个属性就是我们今天要讨论的SameSite属性。

* 值

* * strict
```text
Strict最为严格，完全禁止第三方 Cookie，跨站点时，任何情况下都不会发送 Cookie。
换言之，只有当前网页的 URL 与请求目标一致，才会带上 Cookie。
```

* * lax
```text
Lax规则稍稍放宽，大多数情况也是不发送第三方 Cookie，但是导航到目标网址的 Get 请求除外。
设置了Strict或Lax以后，基本就杜绝了 CSRF 攻击。当然，前提是用户浏览器支持 SameSite 属性。

Chrome 计划将Lax变为默认设置。
这时，网站可以选择显式关闭SameSite属性，将其设为None。
不过，前提是必须同时设置Secure属性（Cookie 只能通过 HTTPS 协议发送），否则无效。
```

* * none

* 现状

Chrome80版本在2020年2月新加入的Samesite特性，将对过往Cookie的默认行为产生新的影响。

对于依赖三方Cookie的业务，比如登录组件，商业化组件等，需要做技术改造来适应Google的这个调整。
Java Web开发底层框架，Servlet的Cookie类还没有支持这个新的属性。

* 未来

希望Google这一举动能反向驱动整个行业生态，共同来根治CSRF漏洞。可以预见3-5年以后，互联网的江湖将不再存在CSRF这个漏洞了。

