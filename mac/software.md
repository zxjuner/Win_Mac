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
* 图片压缩软件，提供 <a href="https://imageoptim.com/mac">Mac 版</a>和网页版，可用 `brew cask install imageoptim` 命令进行安装。

### 5. NetWorker Lite
* 查看实时网速工具，打开 <a href="https://apps.apple.com/cn/app/networker-lite/id1228738830?mt=12">App Store</a> 下载即可。