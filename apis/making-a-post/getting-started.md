# 💫 Getting Started

## Prerequisites

* address
* active address
* apply to ZKEX Team to get `api key` and `api secret`
* depoly `market maker signer service` and send `signer url` to ZKEX Team

***

## Maintain trading pairs information

* Get all trading pairs infomation through the `REST` interface [BnGetProducts](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#bngetproducts)
* Get any trading pair infomation through `ws`, subscribe channel [ws-level2](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#ws-level2)
* When you subscribe to [ws-level2](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#ws-level2) for the first time, you will receive the snapshot data by [push-snapshot](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#push-snapshot)
* When the data of the [ws-level2](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#ws-level2) changes, you will receive the data in the type of [l2update](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#l2update)

***

## REST Interface (Recommend)

### Get the server time of ZKEX

* Http Method : `GET`
* Http Path : `/mm/api/server`
* Response :

***

### Get all trading pairs supported by ZKEX

* Http Method : `GET`
* Http Path : `/mm/api/products`
* Response :

***

### Get Market Maker's JWT-Token (use to subscribe Websocket)

* HTTP Method: `GET`
* HTTP Path: `/mm/api/users` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="154.21167883211677">Name</th><th>Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1653983486</td><td>unix timestamp</td></tr></tbody></table>
*   Response :

    ```
    eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZGRyZXNzIjoiMHgzNDk4ZjQ1NjY0NTI3MGVlMDAzNDQxZGY4MmM3MThiNTZjMGU2NjY2IiwiZXhwaXJlZEF0IjoxNjU0MDU1MDMzLCJpZCI6NDksInB1YmtleSI6IjBkZDRmNjAzNTMxYmQ3OGJiZWNkMDA1ZDllN2NjNjJhNzk0ZGNmYWRjZWZmZTAzZTI2OWZiYjZiNzJlOWM3MjQifQ.2S1wt6KxfJU8kxvESbrdUW1jxYyqxXlcIhL9DwtW3Yc
    ```

***

### Get Market Maker's user info

* HTTP Method: `GET`
* HTTP Path: `/mm/api/self` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="158.21167883211677">Name</th><th>Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1653983486</td><td>unix timestamp</td></tr></tbody></table>
*   Response :

    ```
    {
        "id": 39,
        "address": "0x9f44be256f9b0797dc26bfeed70e57a4ac4258c6",
        "initHeight": 0,     
        "l2active": 1,            // 0: actived in layer2   1：not actived in layer2 
        "l2userId": 67,           // layer2 account id
        "userLevel": "v1",        // fee level
        "verifyType": 0,          // 0: common mode   1: unipass mode
        "chainId": 0              // layer2 chain id (only used in unipass mode)
    }
    ```

***

### Apply Order Slots Batchly

* HTTP Method: `GET`
* HTTP Path: `/mm/api/slot` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="153.21167883211677">Name</th><th>Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1653983486</td><td>unix timestamp</td></tr><tr><td>count</td><td>int</td><td>YES</td><td>1</td><td></td></tr></tbody></table>
*   Response :

    ```
    [
      {
        "slot":  10,             
        "nonce": 100
      }
    ]
    ```

***

### New Order

Send in a new order.

{% tabs %}
{% tab title="Request" %}
* HTTP Method: `POST`
* HTTP Path: `/mm/api/orders` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
* API Limit: A single account is only allowed to send maximum of 30 new order per second

**Parameters:**

<table><thead><tr><th width="166.21167883211677">Name</th><th width="112">Type</th><th width="113">Required</th><th width="159">Example</th><th>Description</th></tr></thead><tbody><tr><td>clientOid</td><td>string</td><td>NO</td><td>1234</td><td>The order id from client</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr><tr><td>side</td><td>string</td><td>YES</td><td>SELL</td><td>SELL/BUY</td></tr><tr><td>type</td><td>string</td><td>YES</td><td>LIMIT</td><td>only support LIMIT now</td></tr><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>timeInForce</td><td>string</td><td>YES</td><td>GTC</td><td>GTC/IOC/GTX/FOK</td></tr><tr><td>quantity</td><td>string</td><td>YES</td><td>20000000000000000000</td><td>decimals=18</td></tr><tr><td>price</td><td>string</td><td>YES</td><td>5000000000000000000</td><td>decimals=18</td></tr><tr><td>takerFeeRatio</td><td>int</td><td>YES</td><td>10</td><td>decimals=4</td></tr><tr><td>makerFeeRatio</td><td>int</td><td>YES</td><td>5</td><td>decimals=4</td></tr><tr><td>slot</td><td>int</td><td>YES</td><td>10</td><td></td></tr><tr><td>nonce</td><td>int</td><td>YES</td><td>310</td><td></td></tr><tr><td>userPubkey</td><td>string</td><td>YES</td><td>0dd4f603531bd78bbecd005d9e7cc62a794dcfadceffe03e269fbb6b72e9c724</td><td>zk-layer2 pubkey</td></tr><tr><td>orderSignature</td><td>string</td><td>YES</td><td>17039d98f87640c452ec4ab6bb91d2044a97ff516a920cd09bddacd774175a28d3836dc0d84c31cc862a1c1099f430adb3f7826bf97a086eba59b6ced3e4ef04</td><td>zk-layer2 signature for order</td></tr></tbody></table>
{% endtab %}

{% tab title="Response" %}
```
{
  "id": "1666371045063401472",
  "createdAt": 1650958799,
  "updatedAt": 1650958799,
  "productId": "UNI-USDT",
  "userId": 1,
  "clientOid": "1234",
  "size": "1000000000000000000",        
  "funds": "70000000",
  "filledSize": "0",
  "executedValue": "0", 
  "price": "70000000", 
  "fillFees": "0",
  "type": "limit",
  "side": "buy",
  "timeInForce": "GTC",     
  "status": "new",
  "l2Status": "none",
  "preSettled": false,
  "settled": false
}   
```
{% endtab %}
{% endtabs %}

***

### Cancel Order

* Cancel an active order
* HTTP Method: `DELETE`
* HTTP Path: `/mm/api/order` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters

    <table><thead><tr><th width="153.21167883211677">Name</th><th>Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr><tr><td>orderId</td><td>int</td><td>YES</td><td>755</td><td></td></tr></tbody></table>
* Response: none

***

### Cancel all Open Orders on a Symbol

* HTTP Meth: `DELETE`
* HTTP PATH: `/mm/api/orders` (HMAC SHA256)
* HTTP HEADER: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="153.21167883211677">Name</th><th>Type</th><th>Required</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr></tbody></table>
* Response : none

***

### Get all orders

* Get all orders, includes `new`, `open`, `filled`, `cancelled`, `cancelling`, `partial`
* HTTP Method: `GET`
* HTTP PATH: `/mm/api/orders` (HMAC SHA256)
* HTTP HEADER: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="143">Name</th><th width="95">Type</th><th width="120">Required</th><th width="116">Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr><tr><td>status</td><td>string</td><td>NO</td><td>filled filled,partial</td><td>The order status (support combined status)</td></tr><tr><td>startTime</td><td>long</td><td>YES</td><td>1</td><td></td></tr><tr><td>endTime</td><td>long</td><td>YES</td><td>1654063467</td><td></td></tr><tr><td>limit</td><td>int</td><td>YES</td><td>20</td><td></td></tr></tbody></table>
*   Response:

    ```
    {
      "total": 1000,
      "orders": [{
        "id": "1666371045063401472",          # order id
        "userId": "28",      # user id
        "price": "9000000000000000",         
        "size": "2500000000",           
        "funds": "19997",                # price*size/pow(10,18)
        "productId": "UNI-USDT",
        "side": "sell",               # buy or sell
        "type": "limit",                
        "createdAt": 1650958799,
        "fillFees": "0",              
        "filledSize": "200000000",                 # The actual transaction quantity of the order
        "executedValue": "1800000",              # The actual transaction value of the order
        "status": "open",                   #order status   `new`, `open`,  `filled`, `cancelled`, `cancelling`, `partial`
        "l2Status": "none",                 #order layer2 status   `none`: init status          `confirming`:The order is fully filled, but not confirmed by layer2      `filled`:The order is fully filled, and confirmed by layer2      `cancelled`:The order has been cancelled, and cancelled in layer2          `partial`:The order is partial filled, and confirmed by layer2
        "preSettled": false,
        "settled": false,
        "chanFrom": 0,             #     0 : user order       1 : market maker order
        "trades": [{
         "id": 1,
         "time": 1650958799,
         "tradeSeq": 231628,
         "price": "9000000000000000",
         "takerOrderId": "1666371045063401472",
         "makerOrderId": "1666371045063401471",
         "size": "100000",
         "side": "buy",
         "status": 3,    # 0:not sent to layer2      1:sent to layer2      2:layer2 success    3:layer2 fail      9:matching fail(not sent to layer2)
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""
        }, {
         "id": 2,
         "time": 1650958799,
         "tradeSeq": 231627,
         "price": "9000000000000000",
         "takerOrderId": "1666371045063401473",
         "makerOrderId": "1666371045063401474", 
         "size": "100000",
         "side": "buy",
         "status": 3,
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""
        }],
        "cancelFill": {
         "id": 1,
         "time": 1650958799,
         "size": "199800000",
         "doneReason": "cancelled"
        }
        "isFullFill": true,   # If isFullFill is true, it means that the order has actually been filled completely. But `trade.status` may not be `filled` , but it will eventually become filled.
       }, {
        "id": "1666371045063401471",
        "userId": "28",      # user id
        "price": "8000000000000000",
        "size": "2500000000",
        "funds": "0",
        "productId": "BTC-USDT",
        "side": "buy",
        "type": "limit",
        "createdAt": 1650958799,
        "fillFees": "0",
        "filledSize": "0",
        "executedValue": "0",
        "status": "cancelled",
        "l2Status": "none",
        "preSettled": false,
        "settled": false,
        "trades": [{
         "id": 1,
         "time": 1650958799,
         "tradeSeq": 231628,
         "price": "8000000000000000",
         "takerOrderId": "1666371045063401471",
         "makerOrderId": "1666371045063401472",
         "size": "100000",
         "side": "buy",
         "status": 3,
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""
        }, {
         "id": 2,
         "time": 1650958799,
         "tradeSeq": 231627,
         "price": "8000000000000000",
         "takerOrderId": "1666371045063401473",
         "makerOrderId": "1666371045063401474",
         "size": "100000",
         "side": "buy",
         "status": 3,
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""
        }]
        "cancelFill": {
         "id": 1,
         "time": 1650958799,
         "size": "199800000",
         "doneReason": "cancelled"
       },
       "isFullFill": true   
      }]
     }    
    ```

***

### Query Order

* Check an order's status.
* HTTP Method: `GET`
* HTTP PATH: `/mm/api/order` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="143">Name</th><th width="95">Type</th><th width="112">Required</th><th width="147">Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr><tr><td>orderId</td><td>int</td><td>YES</td><td>755</td><td></td></tr></tbody></table>
*   Response：

    ```
    {
        "id": "1666371045063401472",    
        "userId": "28",
        "price": "9000000000000000",            
        "size": "2500000000",                
        "funds": "19997",              
        "productId": "UNI-USDT",
        "side": "sell",             
        "type": "limit",                      
        "createdAt": 1650958799,
        "fillFees": "0",                 
        "filledSize": "200000000",                
        "executedValue": "1800000",             
        "status": "open",  
        "l2Status": "none",
        "preSettled": false,
        "settled": false,
        "chanFrom": 0,              
        "trades": [{
         "id": 1,
         "time": 1650958799,
         "tradeSeq": 231628,
         "price": "9000000000000000",
         "takerOrderId": "1666371045063401473",
         "makerOrderId": "1666371045063401474",
         "size": "100000",
         "side": "buy",
         "status": 3,
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""  
        }, {
         "id": 2,
         "time": 1650958799,
         "tradeSeq": 231627,
         "price": "9000000000000000",
         "takerOrderId": "1666371045063401472",
         "makerOrderId": "1666371045063401471", 
         "size": "100000",
         "side": "buy",
         "status": 3,
         "productId": "UNI-USDT",
         "funds": "900",
         "txHash": "0x40acae664609d1115f5ab32d9f3c0fedd7609daa6a4a5515333f583fba10f545",
         "failReason": ""
        }],
        "cancelFill": {
         "id": 1,
         "time": 1650958799,
         "size": "199800000",
         "doneReason": "cancelled"
        },
        "isFullFill": true 
    }
    ```

***

### Get all open orders

* HTTP Method: `GET`
* HTTP Path: `/mm/api/openOrders` (HMAC SHA256)
* HTTP Header: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="143">Name</th><th width="95">Type</th><th width="112">Required</th><th width="147">Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr><tr><td>symbol</td><td>string</td><td>YES</td><td>UNI-USDC</td><td>The trading pair name</td></tr><tr><td>limit</td><td>int</td><td>YES</td><td>20</td><td></td></tr></tbody></table>
* Response : [same as Get all orders Response](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#mmgetorders)

***

### Account Info

* HTTP Method: `GET`
* HTTP Path: `/mm/api/accounts`
* HTTP HEADER: `X-MBX-APIKEY` : `api key`
*   Parameters:

    <table><thead><tr><th width="143">Name</th><th width="95">Type</th><th width="112">Required</th><th width="147">Example</th><th>Description</th></tr></thead><tbody><tr><td>timestamp</td><td>long</td><td>YES</td><td>1654060757</td><td>unix timestamp</td></tr></tbody></table>
*   Response:

    ```
    [
      {
       "id": "1",
       "currency": "USDC",
       "available": "952011220000",
       "hold": "1030410000000"
      }, {
       "id": "2",
       "currency": "USDT",
       "available": "4444030410000000",
       "hold": "766652011220000"
      }
    ]
    ```



