[toc]
# vzone 提供免登录RPC节点服务器
## 1. 节点集群服务域名列表
> - https://rpcnode1.vzone.com （暂未开放）
> - https://rpcnode2.vzone.com （暂未开放）

## 2. 提供RPC方法
```bash
== Addressindex ==
getaddresstxids
getutxoatheight

== Blockchain ==
callcontract "address" "data" ( address )
getbestblockhash
getblock "hash|height" ( verbose )
getblockchaininfo
getblockcount
getblockhash height
getblockheader "hash" ( verbose )
getchaintips
getdifficulty
getmempoolinfo
getrawmempool ( verbose )
gettransactionreceipt "hash"
gettxout "txid" n ( include_mempool )
gettxoutproof ["txid",...] ( blockhash )
gettxoutsetinfo
verifychain ( checklevel nblocks )
verifytxoutproof "proof"

== Clue ==
createclue "address" "inviter" 
createrawcluetransaction "address" "parent" 
getclue "address" 
getcluechildren "clueaddress" 
getclueparent "address" 
getclueparents "address" ("direct") 
getcluetransaction "address" 
getlocalclues 
getluckyclue ("season")

== Contracts ==
addcontract "name" "contractAddress" "abi" "description"
callcontractfunc "contractaddress" "function", "parameters" 
contractfunc2hex "contractaddress" "function", "parameters" 
createcontract "bytecode" (gaslimit gasprice "senderaddress" broadcast)
deploycontract "bytecode" "abi" "parameters" 
fromhexaddress "hexaddress"
getcontractinfo "contractAddress" 
gethexaddress "address"
sendtocontract "contractaddress" "data" (amount gaslimit gasprice senderaddress broadcast)

== Masternode ==
luckymasternodes ("season")
masternodelist ( "mode" "filter" )

== Network ==
getaddednodeinfo ( "node" )
getconnectioncount
getnettotals
getnetworkinfo
getpeerinfo

== Rawtransactions ==
decoderawtransaction "hexstring"
decodescript "hexstring"
fundrawtransaction "hexstring" ( options iswitness )
getrawtransaction "txid" ( verbose )
sendrawtransaction "hexstring" ( allowhighfees )
signrawtransaction "hexstring" ( [{"txid":"id","vout":n,"scriptPubKey":"hex","redeemScript":"hex"},...] ["privatekey1",...] sighashtype )

== Util ==
btcaddresstovds "address"
createmultisig nrequired ["key",...]
estimatefee nblocks
estimatesmartfee conf_target ("estimate_mode")
signmessagewithprivkey "privkey" "message"
v_validateaddress "zaddr"
validateaddress "address"
validatepubkey "pubkey"
verifymessage "address" "signature" "message"

== Vnet ==
getservicelistenstate

```

## 3. 示例

```bash
curl --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaddresstxids", "params": [{"addresses": ["vahhzZdVvWekbEzX2sh99xF9xh3nTGoTyzG"]}] }' -H 'content-type: text/plain;' http://192.168.1.108:9000/

{"result":["da67ddc71f20fa91a78dafa2bc6d2b78632014727329856f3abb004856183a59","0ee243b30a07d747f30d6ad20780807cdabfe637f34def3f337a497128aa8d30","5a3ef5dd25ef2b3d527f85555dfddc3b36d0dd844df9d4905786bf3124eed54a","a445d1760a72f237076a540b2f891094ad208c6f08d7db68e4ceda057e20636b","59fb1485919abfab96b8c96458e72ce0fe127d2e2f83af915a8c3fe9a2f6d44b","1739356c0038dd49032b67da1ef47b527e9778b97d6bb3a7d50dd220134d558a","c29e63c76d5bc3c578848ab5b7f40f61fc172750a62ede49c4bdd95f746398c6","9f8e57a922c3d340c8089cb5ac0cbb9af407cd10e89026185593c59c6f5df7af","a9f335b6907075cd136447443408e95644a16581fa63dda9867288fc121b3ea3","f609dfd4a6abf9aaf006a2b3bb729b578fac3e1a6dfe644e2cd956436966d6ef","977eee710158b89f55a22e2b596f630302ef0ab4ee58cd1483357ccb819de729","83968e9a6f673fbc3fa8efb93d5b077182c3abc4bbcd31dca19fc7c99bf88476","54afb513554133739ddbb271df41d2b6237b06f5e99d3205542b123e2913b095"],"error":null,"id":"curltest"}

curl --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblockchaininfo", "params": [] }' -H 'content-type: text/plain;' http://192.168.1.108:9000/

{"result":{"chain":"regtest","blocks":2245,"headers":2245,"bestblockhash":"8f5c43de2edfd8f507f3614aff6b9ce23f651f3b90a70367d3852c21c1c0bcc1","difficulty":1,"verificationprogress":1,"chainwork":"000000000000000000000000000000000000000000000000000000000000118c","pruned":false,"valuePools":[{"id":"sapling","monitored":false}],"softforks":[{"id":"bip34","version":2,"enforce":{"status":true,"found":1000,"required":750,"window":1000},"reject":{"status":true,"found":1000,"required":950,"window":1000}},{"id":"bip66","version":3,"enforce":{"status":true,"found":1000,"required":750,"window":1000},"reject":{"status":true,"found":1000,"required":950,"window":1000}},{"id":"bip65","version":4,"enforce":{"status":true,"found":1000,"required":750,"window":1000},"reject":{"status":true,"found":1000,"required":950,"window":1000}}],"bip9_softforks":{},"warnings":""},"error":null,"id":"curltest"}


```

