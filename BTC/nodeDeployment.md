# BTC 节点部署

## Ubuntu系统

### 下载bitcoin core

下载地址：https://github.com/bitcoin/bitcoin/releases 

![bticoin-download](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/bitcoin-download.png)

### 建立程序目录

例如：/root/btc

![bitcoin-catalogue](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/bitcoin-catalogue.png)

### 解压bitcoin core

下载的文件上传到btc目录下，并解压，解压命令为：

```
tar -xzvf bitcoin-0.17.1-x86_64-linux-gnu.tar.gz
```

查看存在如下文件

![bitcoin-unzip](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/bitcoin-unzip.png)

### 建立数据目录

建立区块链节点数据存储目录。（目前2019-3-7，BTC区块数据已达到200多个G，注意建立存储目录时要保证硬盘容量够大），本文是直接建立在源码文件解压文件 bitcoin-0.17.1下的，如图：

![bitcoin-data](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/bitcoin-data.png) 

说明：data 是数据存储目录。

### 节点配置

本文是在btc目录下新建的，如图：

![bitcoin-config](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/bitcoin-config.png) 

bitcoin.conf 文件建立的位置可自定义，但是找到文件为位置。

bitcoin.conf 文件内容为(#号为注释符号)：

```
# 数据存储目录（此路径为上面建立的数据储存路径的完整路径）

datadir=/root/btc/bitcoin-0.17.1/data

# 使用测试网络（0：正式网，1：测试网）

testnet=0

# 告知 Bitcoin-Qt 和 bitcoind 接受JSON-RPC命令（是否启用命令和接受RPC服务）

server=1

# 设置 gen=1 以尝试比特币挖矿

gen=0

# 后台执行（是否后台执行）

daemon=0

# 程序运行端口，可修改，默认8332
port=8332

# 监听 RPC 链接,正式默认端口8333 测试默认18333（最好设置好，免得不清楚）

rpcport=8333

#RPC服务账号和密码，不设置的话是有默认密码的，本文没去深究默认，直接用自己设置的

rpcuser=123456

rpcpassword=abcdef

#允许那些IP访问RPC接口，以下写法为默认所有ip都可访问

rpcallowip=0.0.0.0/0

rpcconnect=127.0.0.1

#事务起始索引
txindex=1

```

更多配置可参考网址：https://www.mgchen.com/112.html

本文使用的是简易配置。

### 启动BTC节点程序

本文没有启动后台运行程序，所以建议在服务器开个tmux 启动节点程序。命令为：

```
tmux new -s 1    
```

说明：1为session 名字。

在此目录下执行启动节点程序命令：

```
./bitcoind -conf=/root/btc/bitcoin.conf
```

说明:-conf=/root/btc/bitcoin.conf,此局就是说明按照此配置文件启动节点，文件路径为完完整的文件路径，上面已经说明，此路径可自定义设置，启动节点是需要写明完整路径即可。-txindex=1同步所有交易，包含非钱包交易。

**启动成功后就会自动更新节点数据了。注意：启动BTC节点，包括bitcoin-cli 命令，rpc服务，区块数据同步。**

