# send方法

转账命令

## 参数说明

< input_array>< output_array>< privatekey_array>

- input_array：数组，数组中的每个元素的数据结构如下：
  
  {"txid": \<txid>,"vout": \<vout>}
  
  - txid：交易 ID
  - vout：交易输出索引
  
- outputs_array：数组，数组中的每个元素的数据结构如下：
  {"asset": \<asset>,"value": \<value>,"svalue": \<svalue>,"address": \<address>}
  
  - asset：资产 ID（资产标识符），即该资产在注册时的 RegistTransaction 的交易 ID。其余资产 ID 可以通过CLI命令中的 llist asset 命令查询，也可以在区块链浏览器中查询
  - value：转账金额
  - svalue：转账金额的字符串
  - address：收款地址
  
- privatekey_array：数组，数组中的每个元素的数据结构如下：

  ["privatekey_array1", "privatekey_array2", ...]

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "send",
  "params": [
  		[
  			{
  				"txid": "0x51fe97e4b231b49039cf19f17d6a9ff09b572ec3faf81fefb779c77ee3f5cf12",
  				"vout": 0
  			}
  		],[
  			{
  				"asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
  				"value": "45747514.91248971",
  				"address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
  		],
  		[
  			"b292c761***********d37d40a2"
  		]
  	],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "txid": "0x14fd2e9616896301caea6e805e9d06f961e13c9e483a907dab3f6da7161d4cd4",
        "size": 202,
        "type": "ContractTransaction",
        "version": 0,
        "attributes": [],
        "vin": [
            {
                "txid": "0x51fe97e4b231b49039cf19f17d6a9ff09b572ec3faf81fefb779c77ee3f5cf12",
                "vout": 0
            }
        ],
        "vout": [
            {
                "n": 0,
                "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
                "value": "1",
                "address": "ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY"
            }
        ],
        "sys_fee": "0",
        "net_fee": "0",
        "tx_fee": "0.0001",
        "scripts": [
            {
                "invocation": "40b2c6aa1a600736128f09db0104c98b04ccf4bb7b327cee28ca077bbf14590765fae9762338a6317039c681349c2064e4d60309432e48479eb952721e1da7b25d",
                "verification": "2103855b6f0f748072d0cedaf048e7d0d6cc4ce705d9e7940cbf290e59fd5ec13aa4ac"
            }
        ]
    }
}
```

响应说明：

- 返回如上的交易详情说明交易发送成功
- 交易失败返回error