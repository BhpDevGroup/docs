# BTC API

## 请求模板

### bitcoin-cli

在bin目录执行

bitcoin-cli  -rpcconnect=127.0.0.1 -rpcuser=123456 -rpcpassword=abcdef -rpcport=8332 getnetworkinfo

**注意：-rpcconnect=127.0.0.1 -rpcuser=123456 -rpcpassword=abcdef 这段为配置文件中的内容**

### post请求

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "getnetworkinfo", 
	"params": []
}

### postman工具请求

![1561715552877](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/post-header.png)

第一个框为服务器地址及端口，第二个框为用户名和密码，此为配置文件bticoin.conf中设置的rpcuser和rpcpassword,然后写消息内容如图：

![1561715580139](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/post-body.png)

**更多请求可参考bitcoin的文档或者第三方翻译的文档。**

**Bitcoin文档：https://bitcoin.org/en/developer-reference#remote-procedure-calls-rpcs**

**第三方文档：https://blog.csdn.net/ffzhihua/article/details/80706122**

## API

| method           | description                                                  |
| ---------------- | ------------------------------------------------------------ |
| getnewaddress    | 返回一个用于接收支付的新的比特币地址，如果调用时指定了 账户，那么该地址接收到的支付将计入该账户 |
| getbalance       | 返回钱包中所有账户（或指定账户）的比特币数量，该调用 需要节点启用钱包功能 |
| gettransaction   | 获取指定钱包内交易的详细信息                                 |
| listsinceblock   | 返回指定区块之后发生的与钱包相关的所有交易                   |
| sendtoaddress    | 向指定的地址发送指定数量的比特币                             |
| walletlock       | 打印有关节点和网络的各种信息                                 |
| walletpassphrase | 将钱包解密密钥存储在内存中，存储时间为指定的秒数             |

### getnewaddress

调用返回一个用于接收支付的新的比特币地址，如果调用时指定了 账户，那么该地址接收到的支付将计入该账户。调用需要节点启用钱包支持。

#### 参数

无

#### 返回值

返回一个用于接收支付的新的比特币地址

#### 示例代码

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "getnewaddress", 
	"params": []
}

#### 响应

{
    "result": "344WCRrRKojgmeFacFmiCNZ4cb8QFYshNm",
    "error": null,
    "id": "1"
}

### getbalance

返回钱包中所有账户（或指定账户）的比特币数量，该调用 需要节点启用钱包功能。

#### 参数

- Account：要查看余额的钱包账户，可选，默认值为*，表示全部账户
- Confirmations: 可计入余额的UTXO所需要的最小确认数，可选，默认值：6
- WatchOnlyIncl: 是否包含那些仅用于跟踪的地址，可选，默认值：true

#### 返回值

返回以bitcoin为单位的余额。

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "getbalance", 

​	"params": ["*", 6]

}

#### 响应

{
    "result": 0.00000001,
    "error": null,
    "id": "1"
}

### gettransaction

获取指定钱包内交易的详细信息。该调用需要节点 启用钱包功能。

#### 参数

- TXID：要查看详情的交易ID
- WatchOnlyIncl：是否包含watch-only地址

#### 返回值

返回指定ID的交易的详细信息

- amount：交易金额，正数表示该交易增加钱包余额，负数表示该交易减少钱包余额

- fee：交易手续费，仅针对转出交易

- confirmations：交易确认数，0表示未确认，-1表示存在冲突

- generated：币基交易则该值为true

- blockhash：交易所在区块的哈希

- blockindex：交易所在区块的编号

- blocktime：交易所在区块的unix时间

- txid：交易ID

- walletconflicts：冲突交易数组，成员为冲突交易的ID

- timereceived：节点收到交易的unix时间

- bip125-replacable：是否可替换交易

- comment： 保存在钱包中的交易备注，

- to：保存在钱包中的交易目标备注

- details：输入输出详情数组，成员结构如下：

  - involvesWatchonly：是否包含watch-only地址

    - account：交易影响的账户名称
    - address：对端地址
    - category：交易类别，可以是
      - send：发送交易
        - receive：接收交易
        - generate：成熟币基交易
        - immature：未成熟币基交易
        - orphan：孤儿块中的币基交易

    - amount
    - vout
    - fee
    - abandoned

- hex：串行序列化字符串

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "gettransaction", 

​	"params": ["1075db55d416d3ca199f55b6084e2115b9345e16c5cf302fc80e9d5fbf5d48d"]

}

#### 响应

{

​    "amount" : 0.00000000,

​    "fee" : 0.00000000,

​    "confirmations" : 106670,

​    "blockhash" : "000000008b630b3aae99b6fe215548168bed92167c47a2f7ad4df41e571bcb51",

​    "blockindex" : 1,

​    "blocktime" : 1396321351,

​    "txid" : "5a7d24cd665108c66b2d56146f244932edae4e2376b561b3d396d5ae017b9589",

​    "walletconflicts" : [

​    ],

​    "time" : 1396321351,

​    "timereceived" : 1418924711,

​    "bip125-replaceable" : "no",

​    "details" : [

​        {

​            "account" : "",

​            "address" : "mjSk1Ny9spzU2fouzYgLqGUD8U41iR35QN",

​            "category" : "send",

​            "amount" : -0.10000000,

​            "vout" : 0,

​            "fee" : 0.00000000

​        },

​        {

​            "account" : "doc test",

​            "address" : "mjSk1Ny9spzU2fouzYgLqGUD8U41iR35QN",

​            "category" : "receive",

​            "amount" : 0.10000000,

​            "vout" : 0

​        }

​    ],

​    "hex" : "0100000001cde58f2e37d000eabbb60d9cf0b79ddf67cede6dba58732539983fa341dd5e6c010000006a47304402201feaf12908260f666ab369bb8753cdc12f78d0c8bdfdef997da17acff502d321022049ba0b80945a7192e631c03bafd5c6dc3c7cb35ac5c1c0ffb9e22fec86dd311c01210321eeeb46fd878ce8e62d5e0f408a0eab41d7c3a7872dc836ce360439536e423dffffffff0180969800000000001976a9142b14950b8d31620c6cc923c5408a701b1ec0a02088ac00000000"}

### listsinceblock

返回指定区块之后发生的与钱包相关的所有交易。 该调用需要节点启用钱包功能。

#### 参数

- HeaderHash：区块哈希
- TargetConfirmations：目标确认数，默认值：1
- IncludeWatchOnly：是否包含watch-only地址，默认值：false

#### 返回值

- listsinceblock调用返回一个描述对象，其结构如下：
- transactions：交易数组，成员对象的结构如下：
- involvesWatchOnly：是否包含watch-only地址
- account：账户名称
- address：地址
- category：交易类别：
- send：发送交易
- receive：接收交易
- generate：成熟币基交易
- immature：未成熟币基交易
- orphan：孤儿块币基交易
- amount：数量，负数表示支付，整数表示接收支付
- vout：交易输出序号
- fee：手续费
- confirmations：确认数
- generated：是否币基交易\
- blockhash：区块哈希
- blockindex：区块序号
- blocktime：区块时间戳

- txid：交易id

- walletconflicts：冲突交易数组，成员为交易ID

- time：交易打包时间戳

- timereceived：节点接收到交易时刻的时间戳

- bip125-replaceable：是否可调换交易

- comment：备注信息

- to：目标备注信息

- lastblock： 前一个区块的哈希

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "listsinceblock", 

​	"params": ["0000000099c744455f58e6c6e98b671e1bf7f37346bfd4cf5d0274ad8ee660cb",6, true]

}

#### 响应

{

​    "transactions" : [

​        {

​            "account" : "doc test",

​            "address" : "mmXgiR6KAhZCyQ8ndr2BCfEq1wNG2UnyG6",

​            "category" : "receive",

​            "amount" : 0.10000000,

​            "vout" : 0,

​            "confirmations" : 76478,

​            "blockhash" : "000000000017c84015f254498c62a7c884a51ccd75d4dd6dbdcb6434aa3bd44d",

​            "blockindex" : 1,

​            "blocktime" : 1399294967,

​            "txid" : "85a98fdf1529f7d5156483ad020a51b7f3340e47448cf932f470b72ff01a6821",

​            "walletconflicts" : [

​            ],

​            "time" : 1399294967,

​            "timereceived" : 1418924714,

​            "bip125-replaceable": "no"        

​        },

​        {

​            "involvesWatchonly" : true,

​            "account" : "someone else's address2",

​            "address" : "n3GNqMveyvaPvUbH469vDRadqpJMPc84JA",

​            "category" : "receive",

​            "amount" : 0.00050000,

​            "vout" : 0,

​            "confirmations" : 34714,

​            "blockhash" : "00000000bd0ed80435fc9fe3269da69bb0730ebb454d0a29128a870ea1a37929",

​            "blockindex" : 11,

​            "blocktime" : 1411051649,

​            "txid" : "99845fd840ad2cc4d6f93fafb8b072d188821f55d9298772415175c456f3077d",

​            "walletconflicts" : [

​            ],

​            "time" : 1418695703,

​            "timereceived" : 1418925580,

​            "bip125-replaceable": "no"

​        }

​    ],

​    "lastblock" : "0000000000984add1a686d513e66d25686572c7276ec3e358a7e3e9f7eb88619"}

### sendtoaddress

向指定的地址发送指定数量的比特币。该调用需要节点启用钱包功能

#### 参数

- ToAddress：接收地址

- Amount：发送的比特币数量

- Comment：备注文本

- CommentTo：备注接收人

- AutoFeeSubtract：是否自动扣除手续费，默认值：false

#### 返回值

调用返回交易ID

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "sendtoaddress", 

​	"params": ["1M72Sfpbz1BPpXFHz9m3CdqATR44Jvaydd", 0.1, "donation", "seans outpost"]

}

#### 响应

{
    "result": "a2a2eb18cb051b5fe896a32b1cb20b179d981554b6bd7c5a956e56a0eecb04f0",
    "error": null,
    "id": "1"
}

### walletlock

打印有关节点和网络的各种信息

#### 参数

无

#### 返回值

null

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "walletlock", 

​	"params": []

}

#### 响应

{

​    "result": null,

​    "error": null,

​    "id": "1"

}

### walletpassphrase 

将钱包解密密钥存储在内存中，存储时间为指定的秒数。在钱包已解锁时发出walletpassphrase命令将设置一个新的解锁时间，该时间将覆盖旧的解锁时间。

#### 参数

- passphrase：打开钱包的密码。
- seconds ：解密密钥将自动从内存中删除的秒数，600=10分钟。

#### 返回值

null

#### 示例代码

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "walletpassphrase", 

​	"params": ["my pass phrase", 60]

}

#### 响应

{

​    "result": null,

​    "error": null,

​    "id": "1"

}