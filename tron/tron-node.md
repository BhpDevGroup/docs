# 波场节点搭建

### 一.环境

操作系统：Linux 各类发行版
依赖和工具： JDK 1.8 (请使用Oracle JDK)

### 二.推荐配置

CPU：16核

内存：32G 	

带宽：100M 	

SSD：1T

### 三.部署节点

1.下载最新版本jar包： https://github.com/tronprotocol/java-tron/releases 

2.下载配置文件：https://github.com/tronprotocol/tron-deployment/blob/master/main_net_config.conf 

**配置文件中部分字段说明：**
```
db.engine = "LEVELDB"   数据库类型
```
```
db.directory = "database"    数据名称目录
```

说明：数据目录默认为程序运行时生成的 output-directory 之下，如果要设置数据目录，需要在启动命令中加 -d 参数，如下

```
nohup java -Xmx24g -XX:+UseConcMarkSweepGC -jar FullNode.jar -d /mnt/datassd/trx/node/data -c main_net_config.conf
```

```
listen.port = 18888   程序监听端口
```

```
 http {
    fullNodePort = 8090
    solidityPort = 8091
  }
```
```
fullNodePort = 8090    全节点rpc 端口
```
```
solidityPort = 8091    solidityPort 节点rpc 端口
```

```
rpc {
    port = 50051   
}
```
http/2 rpc 端口 （使用wallet-cli 需要连接，只是节点同步数据可以不开启此端口）



内部交易是指在智能合约中额外执行的一些交易，如call、transfer等。FullNode节点默认配置是不保存内部交易数据，如果需要保存，请设置 

```
saveInternalTx = true
```

启动节点命令：

```
nohup java -Xmx24g -XX:+UseConcMarkSweepGC -jar FullNode.jar  -c main_net_config.conf
```

说明：main_net_config.conf 为下载的配置文件。

### **四.通过节点数据快照导入节点数据**

1.下载节点数据：建议下载 

官方数据源(亚洲:新加坡)	 http://47.74.159.117/	    LevelDB数据，不包含内部交易 (约422G)

其他下载：https://cn.developers.tron.network/docs/%E6%95%B0%E6%8D%AE%E5%BA%93%E5%BF%AB%E7%85%A7%E5%A4%87%E4%BB%BD 

2.解压备份数据库压缩文件至output-directory目录，或者根据自己需求指定解压至相应目录。

**注意：**

LevelDB和RocksDB的数据不允许混用。FullNode通过配置文件的配置项
db.engine 进行指定，可选值为`LEVELDB`或者`ROCKSDB`。


