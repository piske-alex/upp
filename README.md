# upp
Universal Payment Protocal defines a set of REST API to provide a clear and traceable method for payment information to be disseminated and propagated.

## Create order 创建订单
### `POST {api}/gateway/`
参数列表：
``` json
{
  "business_id": 1, //integer
  "amount": 20.34, //float, unit is dollar 以元为单位
  "out_trade_id": "TV3536373" //string, 你的唯一订单号，用于回调
  "signature": md5(business_id+amount+out_trade_id+privteKey) //string privateKey = 密钥
  "notify_url": "https://your_api" //异步回调地址
  "return_url": "https://your_url" //同步返回地址
}

返回讯息：
``` json
{"code_url:"url"} //你可以将用户转到这个地址 
```

### 异步回调
你需要设置你的服务器接收这样的讯息
``` json
{
  "business_id": 1, //integer
  "amount": 20.34, //float, unit is dollar 以元为单位
  "out_trade_id": "TV3536373" //string, 你的唯一订单号，用于回调
  "signature": md5(business_id+amount+out_trade_id+privteKey) //string privateKey = 密钥
}
```
