# GraphQL
```md
GraphQL 是一种 IDL（接口定义语言Interface Definition Language）。
在 2014 年由 Facebook 的工程师团队首次提出。
```md
设计者定义数据类型和并把数据建模为一个图graph，
每个顶点都是一种数据类型的一个实例，边代表了节点之间的关系，这种方式非常灵活，能适应任何业务领域
```
```md
如果说RPC面向过程，REST面向资源，那么GraphQL就是面向数据查询。
```
```md
GraphQL 本质上是“API 的查询语言”。
```
```md
视图定义语言(SDL)，GraphQL有自己的类型系统，用于定义API的Schema。编写Schema的语法称为SDL。
```
## 优势
```md
所见即所得
	查询的返回结果就是输入的查询结构的精确映射
减少网络请求次数
	如果设计的数据结构是从属的，直接就能在查询语句中指定
代码即文档
	GraphQL会把schema定义和相关的注释生成可视化的文档
		从而使得代码的变更，直接就反映到最新的文档上
		避免RESTful中手工维护可能会造成代码、文档不一致的问题。
参数类型强校验
	RESTful方案本身没有对参数的类型做规定，往往都需要自行实现参数的校验机制，以确保安全。
	但GraphQL提供了强类型的schema机制，从而天然确保了参数类型的合法性。
```

## 劣势
```md
问题是设计过程更加复杂，而且传统的数据存储不能很好地映射到图模型
```

## 与RESTful
```md
RESTful的一些不足
	扩展性，单个RESTful接口返回数据越来越臃肿
	某个前端展现，实际需要调用多个独立的RESTful API才能获取到足够的数据
REST对数据的描述形式是一连串的URL端点，而GraphQL则是由相互之间有所关联的schema组成。
相同点
	REST API的URL端点列表与GraphQL的Query/Mutation中的字段类似，都表示数据的访问入口。
	都能用不同的方式描述一个API请求到底是读操作还是写操作。
差异点
	GraphQL让你可以通过一个资源入口访问到关联的其他资源
		只要事先在schema中定义好资源之间的关系即可
		而REST则提供了多个URL端点来获取相关的资源。
	在GraphQL中，Query类型可以在一个请求的根节点中被访问，除此以外它跟其他类型没有区别
		比如你也可以对一个query中的字段添加参数
		而在REST中，即使响应结果是嵌套关系，但在请求中并没有嵌套的概念。
	REST使用POST这样的HTTP方法名称来定义写操作，GraphQL则是查询结构中的关键字。
```
* [对比GraphQL与REST——两种HTTP API的差异](https://www.jianshu.com/p/2ad286397f7a?open_source=weibo_search)

## 注意
```md
GraphQL定义了一种通用的数据查询语言，并不一定要基于HTTP协议
	不过目前绝大部分应用服务器的交互协议都是HTTP
```