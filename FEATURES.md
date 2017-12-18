> 这部分描述了 GeekApk 不同部分的设计特性

## API
> 普通 _HTTP_ WebAPI, 请求地址使用 __URI__ 标准

## API 客户端
### Java
+ [Gson JSON 反序列化](https://github.com/google/gson)
+ [Retrofit](http://square.github.io/retrofit/)

### C#
> 使用 .Net 内建的库

## Android 市场
+ 类似 CoolMarket v7 的界面风格
+ [平滑的动画效果](https://github.com/lgvalle/Material-Animations)
+ Splash 启动屏幕
+ https://github.com/armcha/PlayTabLayout
+ 基于 _BeanShell_ 的设置文件存储

## Android市场插件系统
+ 脚本引擎使用 GeekBsh (一个为 Android 优化/补丁的 BeanShell 引擎, GeekApk 子项目)
+ 采用类似 Java 的 BeanShell 作为钦点的脚本语言
+ Hook 函数没有任何参数, 每次执行脚本时都先清空解释器, 需要的信息用 set(Object) 放置
+ 所有 Hook 默认异步， 调用 __send__ 函数在主线程上进行UI操作. Hook 可以同步， 同步在钩子函数名后添加 __Async__
+ BeanShell 解释器在 __GeekExt__ 初始化时被初始化， 每个 Worker 都是一个 Interpreter, 采用一个解释器一个线程。 当执行线程结束，Worker 回到空闲列表。主线程使用 Handler 接受消息

## 开发者文档
### GeekApk-APIDoc
> 清楚的枚举出所有的 WebAPI 并提供相应返回例子
### GeekApk-ExtensionDev
> 枚举所有钩子和调用方法，如何从头构建一个插件，介绍 BeanShell 脚本语言，提供 __4__ 个插件作为例子

## Mono C# 客户端
+ GTK# GUI
+ 通知系统集成
+ 实现 Android 版本的所有功能

## Mono C# 客户端插件系统
+ 采用预先编译的 C# Assembly 作为模块
+ 默认附带 Roslyn 和 Roslyn 插件以方便传播脚本模式的插件
+ 对于插件提供打开反编译器/调试器的快捷方式
+ 所有 Hook 默认异步, 同步在钩子函数名后添加 __Async__
+ 采用反射来使用模块
###

## API 服务器
+ 基于内存中表 的请求限制
+ 内部机器人用户
+ 统计系统

## Web 客户端和静态页面/额外服务
+ Index 主页
+ Dev 开发者文档主页
+ Services 额外服务页面
+ Sponsors 赞助着页面
+ About 故事

### 额外服务
+ __web.geekapk.com__ Web 客户端
+ __wiki.geekapk.com__ App Wiki
+ __lab.geekapk.com__ (Gitlab) App Lab, 提供 CI 服务
+ *IRC 服务*
+ __pic.geekapk.com__ 图床服务
+ __geekapk.com__ 主页
+ __geekapk.com/dev__ 开发者资源
+ __piwik.geekapk.com__ 统计系统（政治正确化）

### Web
> 实现 Android 版本的所有功能，纯静态，采用质感设计。
