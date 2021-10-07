## Git与Github
- Git简介
    - Git是一款免费, 开源的分布式**版本控制系统**
    - Git可以有效进行项目版本管理
    - Git最初是Linux之父开发用作Linux内核代码的管理.
    - 官网, https://git-scm.com
- Github简介
    - Github是全球最大的社交编程及代码托管网站
    - Github可以托管各种git库, 并提供一个Web页面
    - 作为开源代码库和版本控制系统, 用户量巨大

## 基本概念
- 仓库 Repository
    - 一个仓库就是一个项目
- 收藏 Star
    - 收藏项目的人数
- 复制克隆项目 Fork
- Pull Request
    - 我Fork了一个A的项目, 在上面做了一些改进, 向他发起一个Pull Request, 他会收到消息, 决定是否采用, 如果采用了, A的这个项目中就成了我改进的这个版本
- 关注 Watch
    - 关注了某个项目, 它的任何更新都会向我发送消息通知
- 事务卡片 Issue
    - 讨论一些问题or bug


- Git的工作区域
    - 工作区, Working Directory, 编辑文件
    - git add *
    - 暂存区, 暂存已经修改的文件, 等待统一提交
    - git commit -m "string"
    - Git Repository, 最终确定的文件保存到仓库, 成为一个新的版本
    - git status
## 常用命令行操作
    - git init, 初始化一个git项目, ll .git/, 隐藏文件夹下存放和本地库相关的配置文件
    - 设置签名
        - 作用, 区分不同开发人员的身份
        - 辨析, 这里设置的签名和Github的账户密码没有任何关系, 就是起到一个区分身份的作用.
        - git config --global user.name liws521
        - git config --global user.email 电子邮件名
        - 项目级别/仓库级别, 仅在当前本地库范围有效, 配置信息保存在.git/config文件中, 上述命令去掉global即可配置项目级别
        - 系统用户级别, 登录当前操作系统的用户范围有效, 配置信息保存在~/.gitconfig文件中
        - 就近原则, 有项目级别的用项目级别的, 没有项目级别的用系统用户级别的, 二者都没有是不允许的.
    - git status, 查看工作区, 暂存区状态
    - git add [filename], 将工作区的文件添加到暂存区
    - git commit -m “string” [filename], 将暂存区的内容提交到本地库
    - git log

    - 从git中删除文件, git rm filename
    - 本地仓库提交到远程仓库, git push

# Github Pages搭建网站
- Github Pages仅支持静态网站
- 个人站点
    - 访问https://用户名.github.io
    - 搭建步骤, 创建个人站点仓库名, 用户名.github.io, 在仓库下新建index.html即可
- 项目站点
    - 访问https://用户名.github.io/git库名
    - 原理, git-pages分支用于构建和发布
    - 搭建步骤, 进入项目主页, 点击settings
    - TODO here