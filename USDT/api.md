# USDT API

## 请求模板

### omnicore-cli

在bin目录执行

./omnicore-cli -rpcconnect=127.0.0.1 -rpcuser=bhp -rpcpassword=123456 -rpcport=8335  getblockcount

**注意：-rpcconnect=127.0.0.1 -rpcuser=123456 -rpcpassword=abcdef 这段为配置文件中的内容**

### post请求

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "getblockcount", 
	"params": []
}

### postman工具请求

![1561715552877](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/post-header.png)

第一个框为服务器地址及端口，第二个框为用户名和密码，此为配置文件bticoin.conf中设置的rpcuser和rpcpassword,然后写消息内容如图：

![1561715580139](https://github.com/BhpDevGroup/docs/raw/master/BTC/img/post-body.png)

**支持原有的BTC接口，可参考：https://github.com/BhpDevGroup/docs/blob/master/BTC/api.md**

**第三方文档：http://cw.hubwiz.com/card/c/omni-rpc-api/1/1/1/**

## API

| method                | description                                  |
| --------------------- | -------------------------------------------- |
| omni_getbalance       | 返回指定地址和资产的代币余额                 |
| omni_gettransaction   | 获取指定Omni交易的详细信息                   |
| omni_listtransactions | 返回钱包交易清单，可以使用地址或区块进行过滤 |

### omni_getbalance

返回指定地址和资产的代币余额。

#### 参数

- address：地址，字符串，必需
- propertyid：资产ID，数值，必需

#### 返回值

{
  "balance" : "n.nnnnnnnn",  // (string) the available balance of the address
  "reserved" : "n.nnnnnnnn", // (string) the amount reserved by sell offers and accepts
  "frozen" : "n.nnnnnnnn"    // (string) the amount frozen by the issuer (applies to managed properties only)
}

#### 示例代码

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "omni_getbalance", 
	"params": ["mqpb7ucc41Z9iap7VJsdcKzLji5U2Gd6Fd",2]
}

#### 响应

{
    "result": {
        "balance": "10.00000000",
        "reserved": "0.00000000",
        "frozen": "0.00000000"
    },
    "error": null,
    "id": "1"
}

### omni_gettransaction

获取指定Omni交易的详细信息

#### 参数

- txid：交易哈希，字符串，必需

#### 返回值

{
  "txid" : "hash",                 // (string) 16进制编码的交易哈希
  "sendingaddress" : "address",    // (string) 发送方比特币地址
  "referenceaddress" : "address",  // (string) 作为参照的比特币地址
  "ismine" : true|false,           // (boolean) 交易是否与钱包内某个地址相关
  "confirmations" : nnnnnnnnnn,    // (number) 交易的确认数
  "fee" : "n.nnnnnnnn",            // (string) 交易手续费
  "blocktime" : nnnnnnnnnn,        // (number) 包含交易的区块的时间戳
  "valid" : true|false,            // (boolean) 交易是否有效
  "positioninblock" : n,           // (number) 交易在区块内的序号
  "version" : n,                   // (number) 交易版本
  "type_int" : n,                  // (number) 交易类型代码
  "type" : "type",                 // (string) 交易类型字符串
  [...]                            // (mixed) 其他交易类型相关的属性
}

#### 示例代码

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "omni_gettransaction", 
	"params": ["62577d10a02249db698509cf3d4b060268771b085e3d3fc1e27aeec1cc460d31"]
}

#### 响应

{
    "result": {
        "txid": "62577d10a02249db698509cf3d4b060268771b085e3d3fc1e27aeec1cc460d31",
        "fee": "0.00135538",
        "sendingaddress": "1zgmvYi5x1wy3hUh7AjKgpcVgpA8Lj9FA",
        "referenceaddress": "1NpqmMzYgk5NJ9mBNt24jKAgHGduqdfauG",
        "ismine": false,
        "version": 0,
        "type_int": 0,
        "type": "Simple Send",
        "propertyid": 31,
        "divisible": true,
        "amount": "707.21300000",
        "valid": true,
        "blockhash": "0000000000000000002062b26a7da85f426041a2d9ed91fed29948e60bc927e4",
        "blocktime": 1561963774,
        "positioninblock": 15,
        "block": 583276,
        "confirmations": 1
    },
    "error": null,
    "id": "1"
}

### omni_listtransactions

返回钱包交易清单，可以使用地址或区块进行过滤

#### 参数

- txid：地址过滤器，字符串，可选
- count：返回结果数量，数值，可选，默认值：10
- skip：跳过结果数量，数值，可选，默认值：0
- startblock：检索的起始区块，数值，可选，默认值：0
- endblock ：检索的最后区块，数值，可选，默认值：999999999

#### 返回值

[                                // (array of JSON objects)
  {
    "txid" : "hash",                 // (string) the hex-encoded hash of the transaction
    "sendingaddress" : "address",    // (string) the Bitcoin address of the sender
    "referenceaddress" : "address",  // (string) a Bitcoin address used as reference (if any)
    "ismine" : true|false,           // (boolean) whether the transaction involves an address in the wallet
    "confirmations" : nnnnnnnnnn,    // (number) the number of transaction confirmations
    "fee" : "n.nnnnnnnn",            // (string) the transaction fee in bitcoins
    "blocktime" : nnnnnnnnnn,        // (number) the timestamp of the block that contains the transaction
    "valid" : true|false,            // (boolean) whether the transaction is valid
    "positioninblock" : n,           // (number) the position (index) of the transaction within the block
    "version" : n,                   // (number) the transaction version
    "type_int" : n,                  // (number) the transaction type as number
    "type" : "type",                 // (string) the transaction type as string
    [...]                            // (mixed) other transaction type specific properties
  },
  ...
]

#### 示例代码

{
	"jsonrpc": "2.0", 
	"id":"1", 
	"method": "omni_listtransactions", 
	"params": []
}

#### 响应

{
    "result": [],
    "error": null,
    "id": "1"
}

