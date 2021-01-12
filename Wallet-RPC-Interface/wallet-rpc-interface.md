***\*主要公链的钱包RPC接口\****

**一、*****\*BTC\****

**1．*****\*查钱包余额\****，URL地址：http://127.0.0.1:8332/

（1）请求头（有）

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式（完整的JSON格式）

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "getbalance", 

​	"params": ["*", 1, true]

}

（3）返回格式

{

​	"result": 0.00000001, 

​	"error": null, 

​	"id": "1"

}

**2．*****\*解锁钱包，\****URL：http://127.0.0.1:8332/

（1）请求头

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式

{

​	"jsonrpc": "2.0",

​	"id":"1",

​	"method": "walletpassphrase",

​	"params": ["my pass phrase", 60]

}

（3）返回格式

{

​	"result": null,

​	"error": null,

​	"id": "1"

}

**3．*****\*从钱包转账\****，URL：http://127.0.0.1:8332/

（1）请求头

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "sendtoaddress", 

​	"params": ["mmXgiR6KAhZCyQ8ndr2BCfEq1wNG2UnyG6", 0.1]

}

（3）返回格式

{

​	"result":"a2a2eb18cb051b5fe896a32b1cb20b179d981554b6bd7c5a956e56a0eecb04f0", 

​	"error": null, 

​	"id": "1" 

}

**二、*****\*OMNI-USDT\****

**1．*****\*查钱包余额，\****URL：http://127.0.0.1:8339/

（1）请求头

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "omni_getbalance", 

​	"params": ["mqpb7ucc41Z9iap7VJsdcKzLji5U2Gd6Fd", 31]

}

（3）返回格式

{ 

​	"result": { "balance": "10.00000000", "reserved": "0.00000000", "frozen": "0.00000000" }, 

​	"error": null, 

​	"id": "1"

}

**2．*****\*解锁钱包，URL：\****http://127.0.0.1:8339/

（1）请求头

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式

{

​	"jsonrpc": "2.0",

​	"id":"1",

​	"method": "walletpassphrase",

​	"params": ["my pass phrase", 60]

}

（3）返回格式

{

​	"result": null,

​	"error": null,

​	"id": "1"

}

**1、*****\*从单个地址转账，URL：\****http://127.0.0.1:8339/

（1）请求头

{

​	Username="user",

​	Passsword="pwd"

}

（2）请求格式

{

​	"jsonrpc": "2.0", 

​	"id":"1", 

​	"method": "omni_funded_send", 

​	"params":["1DFa5bT6KMEr6ta29QJouainsjaNBsJQhH","15cWrfuvMxyxGst2FisrQcvcpF48x6sXoH",31, "100.0", "15Jhzz4omEXEyFKbdcccJwuVPea5LqsKM1"]

}

（3）返回格式

{ 

​	"result": "62577d10a02249db698509cf3d4b060268771b085e3d3fc1e27aeec1cc460d31",

​	"error": null, 

​	"id": "1"

}

三、ETH

1、查询单个地址的ETH余额，URL：[http://127.0.0.1:8545/](http://127.0.0.1:8332/)

（4）请求头（无）

{

}

（5）请求格式

{

​	"jsonrpc":"2.0",

​	"id":1, 

​	"method": "eth_getBalance",

​	 "params": ["0xBA2B6ed7815CaC17748843a18EAd8BfF8119A367","latest"]

}

（6）返回格式

{

​	"jsonrpc": "2.0",

​	"id": 1, 

​	"result": "0x16345785d8a0000" 

}

2、转账ETH（A->B），URL：[http://127.0.0.1:8545/](http://127.0.0.1:8332/)

（1）请求头（无）

{

}

（2）请求格式

{

​	"jsonrpc":"2.0", 

​	"id":1, 

​	"method":"eth_sendTransaction", 

​	"params":[{"from":"0xb6cd75af6594f46374378cf3a7d9cbfc06485994",

​	"to":"0x60be0313411e34e8e2ec7094b27a291d827d9b9c",	

​	"gasPrice":"0x3b9aca00",

​	"gas":"0x045",

​	"value":"0x01" },"pwd"]

}

（3）返回格式

{ 

​	"id":1,

​	"jsonrpc": "2.0",

​	"result":"0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331" 

}

3、查询单个地址的USDT_ERC20 余额，URL：[http://127.0.0.1:8545/](http://127.0.0.1:8332/)

（1）请求头（无）

{

}

（2）请求格式

{ 

​	"jsonrpc":"2.0",

​	 "id":1, 

​	"method": "eth_call",

​	"params":[{"to":"0xdac17f958d2ee523a2206206994597c13d831ec7","data":"0x70a08231000000000000000000000000ba2b6ed7815cac17748843a18ead8bff8119a367"},"latest"]

 }

（3）返回格式

{

​	"jsonrpc":"2.0",

​	"id":1,

​	"result":"0x0000000000000000000000000000000000000000000000008ac7230489e80000"

 }

4、转账USDT_ERC20，URL：[http://127.0.0.1:8545/](http://127.0.0.1:8332/)

（1）请求头(无)

{

}

（2）请求格式

{

​	"jsonrpc":"2.0",

​	"id":1,"method":"personal_sendTransaction",

​	"params":	[{"from":"0xba2b6ed7815cac17748843a18ead8bff8119a367","to":"0xdac17f958d2ee523a2206206994597c13d831ec7","value":"0x0","data":"0xa9059cbb000000000000000000000000f67da09bc9671249734f967f55b0d4851a53188a0000000000000000000000000000000000000000000000000de0b6b3a7640000" },

"passwd"]

}

（3）返回格式

{ 

​	"id":1,

​	"jsonrpc":"2.0",

​	"result":"0x8474441674cdd47b35b875fd1a530b800b51a5264b9975fb21129eeb8c18582f" 

}

五、FIL

1、查询单个地址FIL余额，URL：http://192.168.1.174:5001/rpc/v0

（4）请求头

{

​	Authorization="Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBbGxvdyI6WyJyZWFkIiwid3JpdGUiLCJzaWduIiwiYWRtaW4iXX0.fzpHtg9VFX1K8s5vbyrHpGoWYEcJESybHziADoLw5Wc"

}

（5）请求格式

{ 

​	"jsonrpc":"2.0", 

​	"method": "Filecoin.WalletBalance",

​	"params": ["f13sb4pa34qzf35txnan4fqjfkwwqgldz6ekh5trq"], 

​	"id": 3

}

（6）返回格式

{

​	"jsonrpc":"2.0",

​	"result":"710818007035639951586854",

​	"id":3

}

2、转账FIL（A->B），URL：http://192.168.1.174:5001/rpc/v0

（1）请求头

{

​	Authorization="Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBbGxvdyI6WyJyZWFkIiwid3JpdGUiLCJzaWduIiwiYWRtaW4iXX0.fzpHtg9VFX1K8s5vbyrHpGoWYEcJESybHziADoLw5Wc"

}

（2）请求格式

{ 

​	"jsonrpc": "2.0",

​	"method": "Filecoin.MpoolPushMessage",

​	"params": [{"From":"f1zwxnwo2sjpbtw7exsk2uihbk7jg2jbg2ohmozua","To":"f1sewpr36nrb4ji3cpjq34qz7wvpldzkcv7lcizbi","Value":"100000000000000000"}],

 "id": 3

}

（3）返回格式

{

 	"Message": {

​	 "Version": 42,

​	 "To": "f01234",

​	 "From": "f01234",

 	"Nonce": 42,

​	"Value": "0",

​	"GasLimit": 9,

​	"GasFeeCap": "0",

​	"GasPremium": "0",

​	"Method": 1,

​	"Params": "Ynl0ZSBhcnJheQ==",

​	"CID": {

   "/": "bafy2bzacebbpdegvr3i4cosewthysg5xkxpqfn2wfcz6mv2hmoktwbdxkax4s"

 	 }

 },

​	"Signature": {

​	"Type": 2,

​	"Data": "Ynl0ZSBhcnJheQ=="

 	},

 	"CID": {

  		"/": "bafy2bzacebbpdegvr3i4cosewthysg5xkxpqfn2wfcz6mv2hmoktwbdxkax4s"

 		}

}

六、BHP

**1．*****\*查钱包余额\****，URL地址：***\*http://127.0.0.1:20557\****

（1）请求头（否）

{

}

（2）请求格式（完整的JSON格式）

{

 	"jsonrpc": "2.0",

 	"method": "getaccountstate",

 	"params": ["AbkbgybouBAEpkRqfbXAoVXdmsTBRkvCCU"],

​	 "id": 1

}

（3）返回格式

{

  "jsonrpc": "2.0",

  "id": 1,

  "result": {

​    "version": 0,

​    "script_hash": "0x166183cb06300e48257b91de8f29884e7dc724db",

​    "frozen": false,

​    "votes": [],

​    "balances": [

​      {

​        "asset": "0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",

​        "value": "13612224.49651343"

​      }

​    ]

  }

}

 

**2．*****\*转账(从钱包转账)，URL地址: http://127.0.0.1:20557\****

（1）请求头（无）

{

}

（2）请求格式（完整的JSON格式）

{

​	 "jsonrpc": "2.0",

​	"method": "sendtoaddress",

​	"params": ["0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","ATe3wDE9MPQXZuvhgPREdQNYkiCBF7JShY",0.0001],

 	"id": 1

}

（3）返回格式

{

​	"jsonrpc":"2.0",

​	"id":1,

​	"result":{"txid":"0x60170ad03627ce45c7dd56ececbf33b26eab0845aa8b2cbbeecaefc5771b9eb1", 

​	"size": 262, 

​	"type":"ContractTransaction",

​	"version": 0, 

​	"attributes": [], 

​	"vin":[{"txid":"0xd2188c1bd454ac883d79826e5c677deedb91cc61ec6d819df48ff4a963873adb", "vout":1}],

​	"vout":[{"n":0,"asset":"0x13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854","value":"1","address":"AK4if54jXjSiJBs6jkfZjxAastauJtjjse"},{"n":1,"asset":"0x602c79718b16e442de58778e148d0b1084e3b2dffd5de6b7b16cee7969282de7","value":"17.4798197","address": "AWg3L6W68bFfSS13Tf4rt8CRdG2ktaAjGb" } ],

​	"sys_fee":"0",

​	"net_fee":"0",

​	"scripts":[{"invocation":"40a8d40e1652d7ad0c7bb59ef8217237037824af54ee5e46f2fd096c44dd46ef27fa7255010e2a8a2166af8a904e13b96bd3ac82e791633685824c35e7f2731e79","verification":"2102883118351f8f47107c83ab634dc7e4ffe29d274e7d3dcf70159c8935ff769bebac" } ] }

 }