# USDT 节点部署

## Ubuntu系统

参考BTC节点部署

https://github.com/BhpDevGroup/docs/blob/master/BTC/nodeDeployment.md

### 节点配置

USDT与BTC部署到统一台机器上时，注意通过配置文件修改端口及数据文件路径以避免冲突

```
# 数据存储目录

datadir=/root/usdt/data

# 节点连接端口

port=8334

# 监听 RPC 链接,正式默认端口8333 测试默认18333（最好设置好，免得不清楚）

rpcport=8335

```

### 启动BTC节点程序

本文没有启动后台运行程序，所以建议在服务器开个tmux 启动节点程序。命令为：

```
tmux new -s 1    
```

说明：1为session 名字。

在此目录下执行启动节点程序命令：

```
正式网节点：./omnicored  -conf=/root/usdt/bitcoin.conf 
测试网节点：./omnicored  -conf=/root/data/usdt/bitcoin.conf  -testnet  
```

说明:-conf=/root/usdt/bitcoin.conf,此局就是说明按照此配置文件启动节点，文件路径为完完整的文件路径，上面已经说明，此路径可自定义设置，启动节点是需要写明完整路径即可。

**启动成功后就会自动更新节点数据了。注意：启动usdt节点，包括omnicore-cli 命令，rpc服务，区块数据同步。**

### USDT停止程序

./omnicore-cli  -rpcconnect=127.0.0.1 -rpcuser=用户名 -rpcpassword=密码 -rpcport=8335 stop