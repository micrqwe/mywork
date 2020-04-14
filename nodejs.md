
# 参考
* [从Java到Node.js](http://www.ituring.com.cn/article/946)
* [Ghost 基于Node.js的开源博客系统](http://segmentfault.com/a/1190000000372040)
* [How To Install Node.js on an Ubuntu 14.04 server](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server)
* [NODE.JS为什么会成为企业中的首选技术](http://ourjs.com/detail/532f0650c911679a2800000a)
* [PayPal为什么从Java迁移到Node.js，性能提高一倍，文件代码减少44%](http://ourjs.com/detail/52a914f0127c763203000008)
* [who use nodejs?](https://github.com/joyent/node/wiki/Projects,-Applications,-and-Companies-Using-Node)
* [stackedit](https://stackedit.io/)
* [cnodejs](https://cnodejs.org/)
* [nodeschool](http://nodeschool.io/)
* [npm@taobao](https://npm.taobao.org/)


# 安装

## 二进制安装

打开 nodejs 官网的[下载页](https://nodejs.org/download/), 下载二进制安装包
 

```
sudo mkdir /usr/local/nodejs
sudo tar zxvf node-v0.12.1-linux-x64.tar.gz -C /usr/local/nodejs

sudo vi /etc/profile.d/xxx.sh    # 追加以下配置
export NODEJS_HOME=/usr/local/nodejs/node-v0.12.1-linux-x64
export PATH=$NODEJS_HOME/bin:$PATH

cd /usr/local/nodejs/node-v0.12.1-linux-x64
sudo chmod 777 bin
sudo chmod 777 lib/node_modules
```





## Ubuntu

参考[这里](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager)

```
curl -sL https://deb.nodesource.com/setup | sudo bash -
#sudo add-apt-repository ppa:chris-lea/node.js
#sudo apt-get update
apt-cache policy nodejs
sudo apt-get install nodejs
sudo apt-get install build-essential
```


# Http Hello world

新建 hi.js，内容如下

```
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(1337, '127.0.0.1');
console.log('Server running at http://127.0.0.1:1337/');
```

然后运行：

```
node hi.js
```

最后浏览器访问 http://127.0.0.1:1337/



## Centos

使用Linux二进制包。

<del>使用 [nvm](https://github.com/joyent/node/wiki/installing-node.js-via-package-manager#enterprise-linux-and-fedora)</del>

```
su - 
curl -sL https://deb.nodesource.com/setup | sudo bash -
su -
nvm install v0.10.34
```


# npm

## 使用国内淘宝的镜像

* 通过 config 命令

    ```
    npm config set registry https://registry.npm.taobao.org
    npm info underscore
    ```

* 通过命令行参数

    ```
    npm --registry https://registry.npm.taobao.org info underscore
    ```

* 通过修改 `~/.npmrc` 加入以下内容

    ```
    registry = https://registry.npm.taobao.org
    ```

