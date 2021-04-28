# BTC, OMNI, LTC确认说明

### 1.BTC 通过交易ID查询交易详情

请求：
```json
{
	"jsonrpc": "2.0",
	"id": "1",
	"method": "getrawtransaction",
	"params": ["8851fdb3f6e21b4ffcd04f1ce046fccf385cfd5cee42c67ebe31482b1d7131fa", 1]
}
```
返回:
```json
{
	"result": {
		"txid": "8851fdb3f6e21b4ffcd04f1ce046fccf385cfd5cee42c67ebe31482b1d7131fa",
		"hash": "ac9028c56e90bb45ae632beda94dbbe68e2db544c571104227f6562b2e2d0752",
		"version": 2,
		"size": 418,
		"vsize": 256,
		"weight": 1024,
		"locktime": 0,
		"vin": [{
			"txid": "bc35a25729b5aafe4e67147236b8fdbebe9bf09b5addbceee78c0bce6e88170b",
			"vout": 1,
			"scriptSig": {
				"asm": "0014d57c131ee4dc1144dbec98d3b011c937aa03fc73",
				"hex": "160014d57c131ee4dc1144dbec98d3b011c937aa03fc73"
			},
			"txinwitness": ["3044022056655a6ade3f44f4ef47642010e7df001a971ef110335c7fae5730566201ff860220167c30513894dcfb9718499bfe7e4b584b459bce7c5e2932ce9ae81d0df2ef8201", "0342e26fd6533444744a19780aa892e910c3cf3d7b082a92593ea734a68c4fd640"],
			"sequence": 4294967293
		}, {
			"txid": "bc35a25729b5aafe4e67147236b8fdbebe9bf09b5addbceee78c0bce6e88170b",
			"vout": 0,
			"scriptSig": {
				"asm": "0014aa62f693b1b424c980f9f777932ca6bec7537845",
				"hex": "160014aa62f693b1b424c980f9f777932ca6bec7537845"
			},
			"txinwitness": ["304402204903c11bd8abe75f97f29aab55023b209c092573ed7aec055d47ece8174fcc7002201b7c282a449eef5abcb52c6670dd271f3eaae01e70ae67ce0d5cf6e73c543b0301", "02f25e2f4f56bd847061ab0b39093ba44dbede366cbbbc9b6e4f8d97cbc9d11e9b"],
			"sequence": 4294967293
		}],
		"vout": [{
			"value": 0.00005203,
			"n": 0,
			"scriptPubKey": {
				"asm": "OP_HASH160 71320ffc87754783a5c2516dfeb43f7b44543125 OP_EQUAL",
				"hex": "a91471320ffc87754783a5c2516dfeb43f7b4454312587",
				"reqSigs": 1,
				"type": "scripthash",
				"addresses": ["2N3ZkKMsHBKAjbJE2JV92jm6Sjkz5s7YhxC"]
			}
		}, {
			"value": 0.01074326,
			"n": 1,
			"scriptPubKey": {
				"asm": "OP_HASH160 547e741c9953fbef8bfce67dabcdc827b5c1bf0b OP_EQUAL",
				"hex": "a914547e741c9953fbef8bfce67dabcdc827b5c1bf0b87",
				"reqSigs": 1,
				"type": "scripthash",
				"addresses": ["2MzwzEYaFd1KfKNqyRYyV8DyGJZAUg36qHe"]
			}
		}],
		"hex": "020000000001020b17886ece0b8ce7eebcdd5a9bf09bbebefdb8367214674efeaab52957a235bc0100000017160014d57c131ee4dc1144dbec98d3b011c937aa03fc73fdffffff0b17886ece0b8ce7eebcdd5a9bf09bbebefdb8367214674efeaab52957a235bc0000000017160014aa62f693b1b424c980f9f777932ca6bec7537845fdffffff02531400000000000017a91471320ffc87754783a5c2516dfeb43f7b4454312587966410000000000017a914547e741c9953fbef8bfce67dabcdc827b5c1bf0b8702473044022056655a6ade3f44f4ef47642010e7df001a971ef110335c7fae5730566201ff860220167c30513894dcfb9718499bfe7e4b584b459bce7c5e2932ce9ae81d0df2ef8201210342e26fd6533444744a19780aa892e910c3cf3d7b082a92593ea734a68c4fd6400247304402204903c11bd8abe75f97f29aab55023b209c092573ed7aec055d47ece8174fcc7002201b7c282a449eef5abcb52c6670dd271f3eaae01e70ae67ce0d5cf6e73c543b03012102f25e2f4f56bd847061ab0b39093ba44dbede366cbbbc9b6e4f8d97cbc9d11e9b00000000",
		"blockhash": "00000000000000184cc925e3b628fc92ecaadba29769642ba1675f0a711b1f2d",
		"confirmations": 75112,
		"time": 1608021323,
		"blocktime": 1608021323
	},
	"error": null,
	"id": "1"
}
```

交易确认：

- **blockhash 存在**
- **confirmations 大于等于6**

### 2.OMNI-USDT 通过交易ID查询交易详情

请求:
```json
{
	"jsonrpc": "1.0",
	"id": "1",
	"method": "omni_gettransaction",
	"params": ["46f0f7de485ca1e3eb1131364ad983fa3501b342306544311a552d93d51955e9"]
}
```
返回：
```json
{
	"result": {
		"txid": "46f0f7de485ca1e3eb1131364ad983fa3501b342306544311a552d93d51955e9",
		"fee": "0.00002560",
		"sendingaddress": "mhBdwyPcEW91JH4ZZh827C4Zi6BBzc1DdN",
		"referenceaddress": "mpur7dkewdaZdvjq3g4KJqkf1pasG2GpDp",
		"ismine": true,
		"version": 0,
		"type_int": 0,
		"type": "Simple Send",
		"propertyid": 2,
		"divisible": true,
		"amount": "0.00100000",
		"valid": true,
		"blockhash": "00000000a72f8c7f052fd5ab63c0711b437761f777aef618765aaabcd25020f6",
		"blocktime": 1588844035,
		"positioninblock": 37,
		"block": 1723215,
		"confirmations": 249614
	},
	"error": null,
	"id": "1"
}
```
交易确认：

- **blockhash 存在**
- **valid  为 true   (重要)**
- **confirmations 大于等于6**
- **propertyid （正式网为31，测试网为2或1）**

### 3.LTC通过交易ID查询交易详情

请求：
```json
{
	"jsonrpc": "1.0",
	"id": "1",
	"method": "getrawtransaction",
	"params": ["5269cd900690aa52866f8ebe61c1a5e705b58955a6444df774585cab80963861", 1]
}
```
返回：
```json
{
	"result": {
		"txid": "5269cd900690aa52866f8ebe61c1a5e705b58955a6444df774585cab80963861",
		"hash": "28cc2e6332f2b1f2e75ebc5d0756f7c5df70ee9709cc86705af5ac02a9b53ff3",
		"version": 2,
		"size": 172,
		"vsize": 145,
		"weight": 580,
		"locktime": 0,
		"vin": [{
			"coinbase": "030ebd1c0102",
			"sequence": 4294967295
		}],
		"vout": [{
			"value": 12.50189630,
			"n": 0,
			"scriptPubKey": {
				"asm": "OP_HASH160 b685be0a116ccfd860c4379ef33fa3db4ea2e6c2 OP_EQUAL",
				"hex": "a914b685be0a116ccfd860c4379ef33fa3db4ea2e6c287",
				"reqSigs": 1,
				"type": "scripthash",
				"addresses": ["QdF5JnwDWHYMCc34cX81YjniBhMqnp1yGB"]
			}
		}, {
			"value": 0.00000000,
			"n": 1,
			"scriptPubKey": {
				"asm": "OP_RETURN aa21a9ed5128cf4b309e569c66d2cb087085f1a5c50f722be1a0456078f83272447dc885",
				"hex": "6a24aa21a9ed5128cf4b309e569c66d2cb087085f1a5c50f722be1a0456078f83272447dc885",
				"type": "nulldata"
			}
		}],
		"hex": "020000000001010000000000000000000000000000000000000000000000000000000000000000ffffffff06030ebd1c0102ffffffff023e61844a0000000017a914b685be0a116ccfd860c4379ef33fa3db4ea2e6c2870000000000000000266a24aa21a9ed5128cf4b309e569c66d2cb087085f1a5c50f722be1a0456078f83272447dc8850120000000000000000000000000000000000000000000000000000000000000000000000000",
		"blockhash": "303f1e57089f9adb91dd45e780be8c5328fc28180f55164512ec3454002b2422",
		"confirmations": 5,
		"time": 1619590077,
		"blocktime": 1619590077
	},
	"error": null,
	"id": "1"
}
```
交易确认：

- **blockhash 存在**
- **confirmations 大于等于6**