# JSP
```md
JavaServet Pages 是一种实现普通静态HTML和动态页面输出混合编码的技术，类似Microsoft ASP、PHP等技术。
借助内容和外观表现的分离，使得Web页面开发可以方便地划分给页面设计人员和程序员
在运行时态，JSP将会被首先转换成 Servlet，它的效率和功能与Servlet相比没有差别。
```md

* 背景
```md
Servlet和JSP两者分工协作，Servlet侧重于解决运算和业务逻辑问题，JSP则侧重于解决展示问题。
Servlet与JSP一起为Web应用开发带来了巨大的贡献，
后来出现的众多Java Web应用开发框架都是基于这两种技术的，更确切的说，都是基于Servlet技术的。
```

* Servlet 与 JSP
```md
JSP 本质是一个 Servlet，它的运行也需要容器的支持
在 JSP 和 Servlet 文件中都可以编写 Java 和 HTML 代码，不同的是，
Servlet 虽然也可以动态的生成页面内容，但更加偏向于逻辑的控制。
JSP 最终被转换成 Servlet 在 jvm 中解释执行，在 JSP 中虽然也可以编写 Java 代码，但它更加偏向于页面视图的展现。
在 MVC 架构模式中，就 JSP 和 Servlet 而言，C 通常由 Servlet 充当，V 通常由 JSP 来充当。
```