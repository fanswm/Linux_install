## 源码安装
```
cd node-v4.4.2
./configure
make
sudo make install #一定要加sudo
```

- 查看nodejs、npm版本号，确认安装无误
  - 下载安装

    大家可以到 Nodejs 的官网进行下载。下载完成后，执行双击进行运行安装。安装完成后，打开 cmd 命令行，输入 node -v 查看安装的 nodejs 的相关版本信息。

    nodejs -v v4.4.2
    npm -v 2.15.0

- at ezgo linux:
```
      sudo apt-get install nodejs-legacy
      sudo apt-get install npm

      # at ubuntu14.04
      sudo apt-get install nodejs-legacy
      ```

- node.js 镜像配置
```
    # 国内的我推荐大家使用阿里巴巴的镜像地址 http://registry.npm.taobao.org 。执行下面的命令，进行配置。
    npm config set registry http://registry.npm.taobao.org
    
    # 也可以在用户主目录下编辑 .npmrc 文件，添加一行 registry=http://registry.npm.taobao.org 保存就可以了。
```
