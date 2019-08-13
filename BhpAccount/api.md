# API 参考

每个 BHP ACCOUNT 节点 Bhp-CLI 都提供了一套 API 接口，用于从节点获取区块链数据，使得开发区块链应用变得十分方便。接口通过 JSON-RPC 的方式提供，底层使用 HTTP/HTTPS 协议进行通讯。要启动节点，可运行以下命令：

```
dotnet bhp-cli.dll
```

## 修改配置文件

若要通过 HTTPS 的方式访问 RPC 服务器，需要在启动节点前修改配置文件 config.json。

```
{
  "ApplicationConfiguration": {
    "Paths": {
      "Chain": "Chain_{0}"
    },
    "P2P": {
      "Port": 20555,
      "WsPort": 20556
    },
    "RPC": {
      "BindAddress": "127.0.0.1",
      "Port": 20557,
      "SslCert": "",
      "SslCertPassword": ""
    }
  }
}
```

完成配置后打开 BHP-CLI，客户端会在同步到最新区块后自动打开已配置的钱包并进行钱包索引同步。

## 监听端口

JSON-RPC 服务器启动后，会监听 TCP 端口，默认端口如下。

|               | 主网（Main Net） | 测试网（Test Net） |
| ------------- | ---------------- | ------------------ |
| JSON-RPC HTTP | 20557            | 20557              |

## 命令列表

| 方法                                                         | 参数                                             | 说明       |
| ------------------------------------------------------------ | ------------------------------------------------ | ---------- |
| [getnewaccount](https://github.com/BhpDevGroup/docs/blob/master/BhpAccount/api/getnewaccount.md) | [count]                                          | 创建新账户 |
| [send](https://github.com/BhpDevGroup/docs/blob/master/BhpAccount/api/send.md) | < input_array>< output_array>< privatekey_array> | 发送交易   |

## POST 请求示例

一次典型的 JSON-RPC Post 请求的格式如下：

下面以创建账户为例。

请求 URL：

`http://exp.bhpa.io:20557`

请求 Body：

```
{
  "jsonrpc": "2.0",
  "method": "getnewaccount",
  "params": [],
  "id": 1
}
```

发送请求后，将会得到如下的响应：

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

**注：当使用离线同步包同步区块时，程序可能无法响应 API 请求，建议将区块同步到最新高度后再使用 API，否则返回的结果可能不是最新的。**

## 测试工具

你可以用 Chrome 扩展程序中的 Postman 来方便地进行测试（安装 Chrome 扩展程序需要科学上网），下面是测试截图：

![1565687431988](https://github.com/BhpDevGroup/docs/raw/master/asset/%E5%88%9B%E5%BB%BA%E8%B4%A6%E6%88%B7.png)