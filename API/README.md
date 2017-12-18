# GeekApk HTTP API 接口
> [GeekApk 的 HTTP WebAPI 列表](WebAPI.md)

GeekApk 使用 __HTTP API__ 来向服务器请求进行相应操作，大部分操作只需要操作数据库即可完成
目前，API的 _验证_ 部分是通过请求直接比较密码的 Hash 来验证身份，会在稳定以后加以修改

## 大体归类
+ 用户/follow
+ 评论
+ 收件箱
+ Star
+ 评分
+ Splash
+ 新闻
+ 统计
+ 应用
+ 归类
+ bot
+ 讨论
+ tag
+ 管理 ~~权限狗~~
+ 话题（头条）
+ 应用集
+ 私信

部分消耗资源太多的API会有每日请求数目/频率限制，下表列出现在加上的限制:
## 请求限制
