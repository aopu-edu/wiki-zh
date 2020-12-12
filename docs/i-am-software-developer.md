# 开始开发 ScratchHW

## 开发环境

请确保你的计算机已经安装好了以下软件或工具。

- Node >8
- python2.7
- Git

**注意**：如果你是在中国地区或其他网络受限地区，你可能需要购买一个网络代理才能够成功执行下面的操作内容。通过以下指令设置npm的网络代理，将下面的server 和 port 替换为你的代理地址和端口。

```bash
npm config set proxy http://server:port
npm config set https-proxy http://server:port
```

## 克隆&安装

1. 克隆所有工程核心仓库。 (使用```--depth``` 指令来避免下载全部的仓库历史内容，否则GUI的大小将会超过1.18GB)

    ```bash
    mkdir ScratchHW
    cd ScratchHW
    git clone --depth 3 https://github.com/ScratchHW/scratchhw-gui
    git clone --depth 3 https://github.com/ScratchHW/scratchhw-blocks
    git clone --depth 3 https://github.com/ScratchHW/scratchhw-vm
    git clone https://github.com/ScratchHW/scratchhw-link
    git clone https://github.com/ScratchHW/scratchhw-extension-server
    ```
    
2. 安装和链接

    install指令会根据package.json内容下载安装所有必要的npm包，link指令会以本地npm包替换项目内默认的包，这样你在scratchhw-blocks等包中的修改才会被scratchhw-gui使用，否则它默认使用的将会是从npm服务器下载的内容，你可以查看scratchhw-gui/node_modules下的scratchhw-blocks与scratchhw-vm的文件夹，如果link成功，那么他们将被链接到本地克隆下来的工程的位置。
    
    ```bash
    cd scratchhw-blocks
    npm install
    npm link
    cd ..
    cd scratchhw-vm
    npm install
    npm link
    cd ..
    cd scratchhw-gui
    npm install
    npm link scratchhw-blocks scratchhw-vm
    cd ..
    cd scratchhw-link
    npm install
    cd ..
    cd scratchhw-extension-server
    npm install
    cd ..
    ```
    
3. 复制Arduino IDE到路径： `scratchhw-link\tools\Arduino\*`，完成后的文件树结构将如下面所示。

    ```
    scratchhw-link\tools\
    |- Arduino\
      |- drivers\
      |- examples\
      |- hardware\
      |- java\
      ...
      |- arduino.exe
      |- arduino_debug.exe
    ```

## 运行

1. 启动硬件接口服务器 scratchhw-link

    ```bash
    cd scratchhw-link
    npm start
    ```

2. 启动插件内部服务器 scratchhw-extension-server

	在新的一个终端中执行。

    ```bash
    cd scratchhw-extension-server
    npm start
    ```

3. 启动 scratchhw-gui

	在新的一个终端中执行。

    ```bash
    cd scratchhw-gui
    npm run start-open
    ```

4. 在scratchhw-gui的webpack构建完成后，将会有弹出scratchhw-gui的网页，开始使用吧~。当然你也可以通过手动输入地址 `http://127.0.0.1:8601/` 来访问。

## 了解更多开发内容

1.  [构架介绍](./software-developer-reference/framework-introduction.md) 

2. [如何添加新的设备](./software-developer-reference/how-to-add-a-new-device.md) 

3. [如何添加新的扩展](./software-developer-reference/how-to-add-a-new-extension.md)