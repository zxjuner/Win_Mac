# Mac下git多账户配置

1. 首先检查以前是否设置好用户名邮箱信息，即是否执行过：
```
git config --global user.name "注册用户名"
git config --global user.emall "注册邮箱"
```
使用命令查看：`git config --list` 查看是否有 `user.name` 和 `user.email` 信息，如果没有，忽略此步；如果有，使用如下命令清除：
```
git config --global --unset user.name
git config --global --unset user.email
```

2、生成 SSH key
```
ssh-keygen -t rsa -C "xxx@xx.com”
```
回车后会有如下提示：
```
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/{username}/.ssh/id_rsa):
```
提示输入生成的 ssh key 的存储路径和名称；如果是简单的配置一个账号，直接回车，自动取默认路径和名称，默认为 id_rsa。如是为多个 git 账号配置私钥/公钥，需指定路径和名称，且需重命名秘钥文件名。例如：
```
Generating public/private rsa key pair.  
Enter file in which to save the key (/Users/{username}/.ssh/id_rsa): /Users/{username}/.ssh/id_rsa_gitlab
```
再按两次回车，默认密码为空。
将上面 ssh 密钥生成步骤重复一次，添加两个 git 账户，例如得到四个文件为：
  - id_rsa、id_rsa.pub
  - id_rsa_gitlab、id_rsa_gitlab.pub

执行 `cd ~/.ssh` 切换到 .ssh 目录，然后执行 `ls` 可查看生成的秘钥。

3、将新生成的两个公钥中的内容分别添加配置到 GitHub 或 Gitlab 等要配置的账户中。可用 `cat id_rsa_gitlab.pub` 命令查看 id_rsa_gitlab.pub 中的内容。

4、将秘钥添加到高速缓存中：
因为默认只读取 id_rsa，为了让 SSH 识别新的私钥，需将其添加到 SSH agent 中，这样在当前会话中就不需要再次输入密码了。例：
```
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_rsa_gitlab
```
查看是否添加成功：`ssh-add -l`

5、添加配置文件设置（为防止提交失败等问题）
查看 .ssh/ 目录下是否存在 config 文件，如果不存在，创建：`touch config`
打开添加如下内容，例：
```
#github
Host github_username    //别名
  HostName github.com    //连接域名
  user {username}    //账户
  IdentityFile ~/.ssh/id_rsa    //对应私钥

#gitlab
Host gitlab_username    //别名
  HostName gitlab.com    //连接域名
  user {username}    //账户
  IdentityFile ~/.ssh/id_rsa_gitlab    //对应私钥
```
6、验证 Git 连接
```
ssh -T git@github.com 
Hi XXXX! You've successfully authenticated, but GitHub does not provide shell access.
```
说明 GitHub 已连接成功。
如果连接不成功，用如下命令查看出错信息：
```
ssh -vT git@gihub.com
```

7、仓库配置
因为清除了全局用户名和邮箱，需要给每个仓库单独配置用户名信息，进入该仓库后，执行：
```
git config --local user.name "XXXX"
git config --local user.email "XXXX@qq.com"
```

执行后，通过以下命令查看本仓库的配置信息：
```
git config --local --list
```
