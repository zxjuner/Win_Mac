# Gitbook

1. 安装 (基于 node, 版本过高有可能安装失败)：

    ```bash
    npm install -g gitbook-cli
    ```

2. 使用：
    - 安装插件:  gitbook install <packageName>
    - 升级到新版:  gitbook update
    - 初始化仓库:  gitbook init
    - 启动本地服务:  gitbook serve
    - 修改后重新构建服务:  gitbook build
    - 生成 PDF、epub、mobi (需下载安装 Calibre):  gitbook pdf

        ```bash
        brew install calibre
        sudo ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin
        ```