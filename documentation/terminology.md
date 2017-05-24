# 术语表

### 服务消费者
向另一组件（服务`提供者`）发起HTTP请求的组件。注意这并不依赖于数据的流动方式——无论是`GET`还是`PUT` / `POST` / `PATCH`，`消费者`都是HTTP请求的发起者。

### 服务提供者
向另一组件（服务消费者）的HTTP请求提供响应的服务器。

### 模拟的服务提供者
在`消费者`项目中的单元测试里用于模拟真实的服务`提供者`，意味着不必需要真实的服务`提供者`就绪，就可以将类集成测试运行起来。

### Pact文件
一个包含了将`消费者`测试中所定义的请求和响应序列化为JSON形式的文件。即`契约`。

### Pact验证
要对一个`Pact`进行验证，就要对`Pact`文件中所包含的请求基于`提供者`代码进行重放，然后检查返回的响应，确保其与`Pact`文件中所期望响应相匹配。

### 提供者状态
在对提供者重放某个给定的请求时，一个用于描述此时`提供者`应处于的“状态”（类似于夹具）的名字——比如“when user John Doe exists”或“when user John Doe has a bank account”。

`提供者`状态的名字是在写`消费者`测试时被指定的，然后当运行`提供者`的pact验证时，这个名字将被用于唯一标识在请求被执行前应该运行的代码块。

### Pact规范

[Pact规范](https://github.com/pact-foundation/pact-specification)是一份用于管理实际生成的Pact文件结构的文档，以满足不同语言之间的互操作性（例如，设想一个JavaScript实现的`消费者`连接到基于Scala JVM的`提供者`），使用语义版本控制来指示具有破坏性的变化。

Pact在每种语言下的实现都要实现规范中的规则，并且明确说明支持哪个或哪些版本，主要对应于哪些特性是可用的。

该规范的当前版本是[2.0](https://github.com/pact-foundation/pact-specification/tree/version-2)，虽然目前还未能让各种实现全部支持该版本。