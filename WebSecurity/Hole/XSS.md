# XSS

跨站脚本攻击（Cross Site Scripting）。

## 漏洞类型

### 存储型 XSS 漏洞（风险等级：高）

* 漏洞危害
存储 XSS 把用户输入的数据存储到数据库，显示到前端页面。攻击者可进行身份验证盗取和蠕虫攻击。
存储型XSS也叫做“持久型XSS”

### 反射型

* 漏洞危害
反射型 XSS 把用户输入的数据“反射”给浏览器。攻击者往往需要诱使用户“点击”一个恶意链接，才能攻击成功。
反射型XSS也叫做“非持久型XSS”。

## 修复办法

```text
1. 使用HttpOnly有助于缓解XSS攻击
    但是在部署时需要注意，如果业务复杂，则需要在所有Set-Cookie的地方，给关键Cookie都加上HttpOnly。
    漏掉了一个地方，都可能使得这个方案失效。
2. 在服务器端对输入进行格式检查
    如在网站注册时填写的用户名只能为字母、数字的组合，手机号应该是不长于16位的数字
    检查输入中是否包含一些特殊字符，如<、>、'、"、/等，如果发现，则进行过滤或编码
    对输入进行XSS特征的匹配，如查找数据中是否包含“script”、“javascript”、“prompt”、“confirm”等敏感字符。
3. 一般来说，除了富文本的输出外，在变量输出到HTML页面时，可以使用编码或转义的方式来防御XSS攻击。
    针对HTML代码的编码方式是HtmlEncode，在PHP中，有htmlentities()和htmlspecialchars()两个函数可以满足安全要求。
    相应的，JavaScript的编码方式可以使用JavascriptEncode，JavascriptEncode与HtmlEncode的编码方式不同，它需要使用“\”对特殊字符进行转义。
    在对抗XSS时，还要求输出的变量必须在引号内部，以避免造成安全问题；除了HtmlEncode、JavascriptEncode外，还有很多用于各种情况的编码函数，比如XMLEncode、JSONEncode等
```