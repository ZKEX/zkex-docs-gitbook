# 📌 Websocket Data Push

## Overview

***

### Snapshot data

* Subscribe channel : `level2`
* Push only once, when the `level2` channel is established

***

### Data changes

* Subscribe channel : `level2`

```
  {
   "type": "l2update",
   "productId": "UNI-USDC",
   "time": 1686645711,
   "changes": [
     [
       "sell",
       "90000000000000000000",  // price
       "100000000000"     // amount
     ]
   ]
  }
```

***

### K-line data

* Subscribe channel: `candles_1m`,`candles_3m`,`candles_5m`....
* Maximum 1 push within 1s

```
{
 "type": "candles_1m",
 "productId": "UNI-USDC",
 "time": 1653273480,
 "open":  "1100000000000000000",          
 "close":  "1100000000000000000",          
 "low":  "1100000000000000000",            
 "high": "1100000000000000000",           
 "volume": "10000000000000000000"          
}
```

***

### Ticker info

* Subscribe channel: `match`
* Maximum 1 push within 3s

```
{
 "type": "ticker",
 "tradeSeq": 20,
 "sequence": 85,
 "time": 1650958799,
 "productId": "UNI-USDC",
 "price": "90000000000",      
 "side": "sell",       
 "lastSize": "10000000",
 "bestBid": "",
 "bestAsk": "",
 "volume24h": "110000000000000000", 
 "volume30d": "310000000000000000", 
 "low24h": "1000000000000000",     
 "high24h": "1000000000000000",    
 "open24h": "1000000000000000",
 "close24h": "1000000000000000"    
}
```

***

### Matching info

* Subscribe channel: `match`
* Since the settlement of ZKEX is in Layer 2, `match` only means that the matching is successful, not that the transaction is successful

```
{
 "type": "match",
 "tradeSeq": 20,
 "sequence": 100,
 "time": 1650958799,
 "productId": "UNI-USDC",
 "price": "900000000000",
 "size": "1000000000",
 "makerOrderId": "1666371045063401472",     # maker's order id
 "takerOrderId": "1666371045063401471",     # taker's order id
 "side": "sell"
}
```

***

### Trading info

* Subscribe channel: `trade`
* After the `match` channel is pushed, if layer2 is actually done, the `trade` channel will be pushed.

```
{
 "type": "trade",
 "tradeSeq": 20,
 "time": 1650958799,
 "productId": "UNI-USDC",
 "price": "900000000000",
 "size": "1000000000",
 "makerOrderId": "1666371045063401472",     # maker's order id
 "takerOrderId": "1666371045063401471",     # taker's order id
 "side": "sell",
 "status": 2,
 "failReason": ""
}
```

***

### Order change infomation of a trading pair

* Subscribe channel: `order`

```
{
 "userId": 1,
 "clientOid": "1234",
 "type": "order",
 "sequence": 0,
 "id": "50",
 "price": "1000000000",
 "size": "1000000000000",
 "funds": "0",
 "productId": "UNI-USDC",
 "side": "sell",
 "orderType": "limit", 
 "createdAt": 1650958799,
 "fillFees": "0",         # fee (calculated in quote tokens)
 "filledSize": "0",       # number of successfully matched (calculated in base tokens)
 "executedValue": "0",     # value of successfully matched (calculated in quote tokens)
 "status": "new",      # order status:   `new`, `open`, `filled`, `cancelled`, `cancelling`, `partial`
 "settled": false,     # whether the matching was successful
 "timeInForce": "GTC"     
}
```

***

### The asset change information of an account

* Subscribe channel: `funds`

```
{
 "type": "funds",
 "sequence": 0,
 "userId": "1",
 "currencyCode": "UNI",
 "available": "820900000000000000", 
 "hold": "11741000000000000000"  
}
```
