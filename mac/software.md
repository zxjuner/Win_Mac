## Mac 常用软件
### 1. Xcode
打开 <a href="https://apps.apple.com/cn/app/xcode/id497799835?mt=12">Apple Store</a> 下载即可
* commandline tools
    - 打开 Xcode，file -> project -> os x application -> Command Line
Tool，如果已经存在，代表已经安装
    - 命令行安装:  `xcode-select --install`
    - 卸载: `sudo rm -rf /Library/Developer/CommandLineTools`

### 2. Homebrew
* Homebrew 是 Mac OS 上的软件包管理工具，能在 Mac 中方便的安装或卸载软件。
* Homebrew 官方网站：https://brew.sh
* 常用命令：
```
brew install <packageName>      # 安装软件
brew uninstall <packageName>    # 卸载软件
brew search <packageName>       # 查询软件
brew upgrade name               # 更新已安装软件
brew list                       # 列出已安装软件
brew update                     # 更新 brew
brew home                       # 打开 brew 官网
brew info <packageName>         # 显示软件信息
brew deps                       # 显示包依赖
brew cleanup                    # 清除下载缓存
```
* Homebrew Cask 是 Homebrew 的扩展，借助它可以方便地在 macOS 上安装图形界面程序，brew cask的常用命令：
```
brew cask install name      # 下载安装软件
brew cask upgrade name      # 更新软件
brew cask uninstall name    # 卸载软件
brew cask info app          # 列出应用的信息
brew cask list              # 列出本机安装过的软件列表
brew cask cleanup           # 清除下载的缓存以及各种链接信息
```

### 3. Sublime Text
* Sublime Text 官方网站：https://www.sublimetext.com ，可用 `brew cask` 进行安装。
* 安装 Package Control：
	+ https://packagecontrol.io/installation
	+ 常用插件安装：https://packagecontrol.io
	+ 常用插件：
		* Color Highlighter
		* Emmet
		* HTML-CSS-JS Prettify

### 4. ImageOptim
* 图片压缩工具，提供 <a href="https://imageoptim.com/mac">Mac 版</a>和网页版，可用 `brew cask install imageoptim` 命令进行安装。

### 5. NetWorker Lite
* 查看实时网速工具，打开 <a href="https://apps.apple.com/cn/app/networker-lite/id1228738830?mt=12">App Store</a> 下载即可。

### 6. Aria2
* 介绍：下载工具
* 安装：`brew install aria2`
* 配置：创建并修改配置文件于此路径 `~/.aria2/aria2.conf`
```
cd -
mkdir .aria2
cd .aria2
touch aria2.conf
```
* aria2.conf 配置示例（参考自 <a href="http://aria2c.com/usage.html">http://aria2c.com/usage.html</a> ）：
	- 第一行的 `XXX` 改为自己电脑用户名
```
dir=/Users/XXX/Downloads
continue=true
max-concurrent-downloads=5
max-connection-per-server=5
min-split-size=10M
split=5
disable-ipv6=true
input-file=/usr/local/Cellar/aria2/aria2.session
save-session=/usr/local/Cellar/aria2/aria2.session
enable-rpc=true
rpc-allow-origin-all=true
rpc-listen-all=true
listen-port=51413
enable-dht=false
enable-peer-exchange=false
peer-id-prefix=-TR2770-
user-agent=Transmission/2.77
seed-ratio=0
bt-seed-unverified=true
bt-save-metadata=true
```
* 网页UI：<a href="http://binux.github.io/yaaw/demo/">http://binux.github.io/yaaw/demo/</a>，配置 `JSON-RPC Path` 为：`http://localhost:6800/jsonrpc`

### 7. node 版本管理工具 nvm
可使用 Curl 或 Wget 安装，Curl 和 Wget 的安装方法如下：
```
brew curl
brew wget
```
Curl:
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
Wget:
```
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```
* 注意：
如果出现 `command not found`，在配置文件中添加：
```
#for nvm command not found
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" #This loads nvm bash_completion
```

* 常用命令

```
nvm install stable      # 安装最新稳定版 node

nvm install 8.9.4       # 安装 8.9.4 版本

nvm use 8.9.4           # 切换至 8.9.4 版本

nvm use node            # 切换至最新版本

nvm alias default 8.9.4 #设置默认 node 版本为 8.9.4

nvm current             # 查看当前版本

nvm uninstall 8.9.4     # 卸载指定版本

nvm ls                  # 查看已安装版本
```