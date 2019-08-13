# getnewaccount方法

创建账户

## 参数说明

count：创建账户的个数，默认为1.

## 调用示例

请求正文：

```
{
  "jsonrpc": "2.0",
  "method": "getnewaccount",
  "params": [],
  "id": 1
}
```

响应正文：

```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "wif": "L3CqLKy2iJ***********HMnWytytT",
            "prikey": "b292c761***********d37d40a2",
            "pubkey": "03cdfbd7e947021a955e2258c0fc4782dd60b09f2b3fca5a4ccdb1902d5dd8707b",
            "address": "ARdcUDE8B5LHBkzeK88KsLM3k9xtYbnhFZ"
        }
    ]
}
```

响应说明：

- wif：账户的wif
- prikey：账户的私钥
- pubkey：账户的公钥
- address：账户的地址