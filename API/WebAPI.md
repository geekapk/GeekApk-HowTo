# GeekApk WebAPI
> Version 0.0.1 第一个 API 设计协定

### 大体功能|数据存储
+ 用户， 包含 ID, 用户名, 邮箱, bio, Github/Gitlab ID, Hash, 创建时间和上线时间， 屏蔽用户
+ 评论，uid id t`(arget)`id text reply`(to id)` edited? time
+ 收件箱，uid tid id time optr`(操作人)`
+ Star，uid tid id time
+ Rate，uid tid level`(0-9)`
+ 新闻，uid id text optr time
+ 应用，uid id title`(梗概)` name class`(分类)` news`(what's new?)` desc`(ription)` license shots`(screenshots)(Other Table)` blame`(点评)` count icon dl`(链接)` ver`(sion)` time
+ 分类，id name desc super`(category ID)`

### 操作
#### 用户
> user|uid name mail bio ghid glid hash ctime atime

> user_block|uid t_user

|name|desc|
:--|:--
uid|用户 `ID`, 从 _0_ 开始计数， 每新建一个用户 `last_id` 表中的特殊 uid 记录的值自增
name|用户名, 最大长度 _30_ 个字符
mail|邮箱, 不进行验证, 最大长度 _90_ 个字符 _(对内部没有必要正确, 但必须符合 user '@' host 格式)_
bio|用户的自我介绍, 最长 _900_ 个字符
ghid|GitHub ID, 必须正确设置或者为空 
glid|GitLab ID, 必须正确设置或者为空, 和 `ghid` 必须有一项不为空
hash|验证身份时比较的 Hash 数值, 为用户密码的 sha-256 Hash
ctime|用户创建时间
atime|用户上线时间 (客户端自动更新)
t_user|被 `block` 的用户 ID, `0.0.1` 中暂时不实现这个特性

##### Create
+ 使用 GitHub/GitLab 的 Gist 验证 创建用户: name, initial hash(客户端根据密码生成), gist id, auth
> 如果 gist 上的 auth hash 后与 auth 匹配，则验证通过

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
uid|用户 ID
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
##### Create
##### Read
##### Update
##### Delete

#### Star
##### Create
##### Read
##### Update
##### Delete

#### Rate
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
