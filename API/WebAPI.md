# GeekApk WebAPI
> Version 0.0.1

### 大体功能
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
##### Create
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
