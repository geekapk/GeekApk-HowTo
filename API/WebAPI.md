# GeekApk WebAPI
> Version 0.0.1 第一个 API 设计协定

### 数据存储与交互
- User - 存储用户个人信息，提供用户信息和认证接口
- Topic - 存在讨论区功能的数据对象
- App extends Topic - 应用
- Article extends Topic - 用户发表的文章
- AppCategory extends Topic - 应用类别
- Discussion - （讨论区）讨论内容项
- Rating - （讨论区）用户评分记录
- Favorite - 用户收藏的应用

### 数据对象
#### User

##### 存储

表: users

名称| 类型 | 是否必需 | 描述
:--|:--|:--|:--
id | char(36) | required | 用户 UUID. 由 OneIdentity 提供.
name | varchar(256) | required | 用户名. 由 OneIdentity 提供.
display_name | varchar(256) | required | Profile 等位置显示的用户名称. 首次登录时设置.
mail | varchar(256) | optional | 邮件地址.
bio | text | optional | 自我介绍, 最长 _900_ 个字符.
create_time | bigint | required | 首次登录时间.

##### 登录流程
1. 客户端通过 OneIdentity 基本身份认证流程获得 Basic Identity Token.
2. 客户端向 GeekAPK 服务器提交 Basic Identity Token.
3. 服务器对客户端提交的 Token 进行验证，并获取用户的基本信息. 生成并下发 GeekAPK Access Token 和账户状态.
4. 客户端保存 GeekAPK Access Token, 并检查账户状态。如果账户已经完成 GeekAPK 个人信息初始化，则重定向至登录前的页面或个人信息页；否则，引导用户完成个人信息初始化。

---

##### Read
###### By UID
+ username
+ mail
+ bio
+ github/gitlab ID
+ ctime/atime

###### Gets UID/ UID list
+ username _(WC)_
+ mail/mail domain _(WC)_
+ bio _(WC)_
+ github/gitlab ID
+ ctime/atime range

##### Update _(Auth needed)_
+ username
+ mail
+ bio
+ Github/Gitlab ID _(Gist auth needed)_
+ Hash _(Gist auth needed)_
+ ctime

##### Delete
+ delete user _(Auth needed) (Gist auth needed) (limited)_

#### 评论
> reply|uid id tid text reply edited time

name|desc
:--|:--
uid|评论者用户 ID
id|reply ID
tid|目标 ID, 用于区分目标。TID 一般为应用的 ID, 但是有一些预留的 TID 用于指定没有回复评论功能的一些评论目标(比如 news), 这种情况下 `reply ID` 就是相应目标的 ID
reply|回复目标，一般是一个 _reply_ 的 _ID_, 但在特殊 _TID_ 时这个字段用于指示特殊目标的 ID
edited|编辑时间
time|创建时间, 一般也用于按时间排序模式

##### Create
> 使用 _用户验证(uid+对应hash)_ 和
+ tid
+ reply (如果不是特殊 TID 可为空)

创建一条评论

##### Read
##### Update
##### Delete

#### 收件箱
> post|uid tid id time optr

name|desc
:--|:--
uid|收件用户 ID
tid|目标 ID
id|配合 `tid` 用于明确指示目标
time|发送时间
optr|操作人, 必须是有效 `uid`

##### Create
##### Read
##### Update
##### Delete

#### Star
> star|uid tid id time

name|desc
:--|:--
uid|操作用户 ID
tid|目标 ID
id|配合 `tid` 用于明确指示目标
time|操作时间

##### Create
##### Read
##### Update
##### Delete

#### Rate
> rate|uid appid level

name|desc
:--|:--
uid|操作用户 ID
appid|应用 ID
level|打分

> 目前的设计是只允许给应用打分，如果觉得不妥请开 [issue](https://github.com/duangsuse/GeekApk-HowTo/issues) 讨论

##### Create
##### Read
##### Update
##### Delete

#### 新闻
##### Create
##### Read
##### Update
##### Delete

#### 应用
##### Create
##### Read
##### Update
##### Delete

#### 分类
##### Create
##### Read
##### Update
##### Delete

#### 特殊 ID
> 这是内部硬点的保留 ID 列表，用于在不同的表中表示特殊意义，只和 API 版本有关

id|desc
:--|:--
0|
1|
2|
3|
4|
5|
