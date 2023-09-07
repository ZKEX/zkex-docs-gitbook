# 🤍 Websocket Subscribe & Unsubscribe

### Order data of any trading pair (`level2`)



{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "level2"
  ],
  "token": "" #option
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "level2"
  ],
  "token": "" #option
}
```
{% endtab %}
{% endtabs %}

**Notice:**

When you subscribe to [level2](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#ws-level2) for the first time, you will receive the snapshot data by [push-snapshot](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#push-snapshot)

***

### K-line data of a trading pair (1/3/5/15/30/60min/2/4/6/12/24hour)



{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "candles_1m"
  ],
  "token": ""   # optional (JWT-token)
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "candles_1m"
  ],
  "token": ""    # optional (JWT-token)
}
```
{% endtab %}

{% tab title="Channel name comparison table" %}
<table><thead><tr><th width="309">channel name</th><th>time</th></tr></thead><tbody><tr><td>candles_1m</td><td>1min</td></tr><tr><td>candles_3m</td><td>3min</td></tr><tr><td>candles_5m</td><td>5min</td></tr><tr><td>candles_15m</td><td>15min</td></tr><tr><td>candles_30m</td><td>30min</td></tr><tr><td>candles_60m</td><td>60min</td></tr><tr><td>candles_120m</td><td>2hour</td></tr><tr><td>candles_240m</td><td>4hour</td></tr><tr><td>candles_360m</td><td>6hour</td></tr><tr><td>candles_720m</td><td>12hour</td></tr><tr><td>candles_1440m</td><td>24hour</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

***

### Ticker info of a trading pair

{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "ticker"
  ],
  "token": ""    # optional (JWT-token)
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "ticker"
  ],
  "token": ""    # optional (JWT-token)
}
```
{% endtab %}
{% endtabs %}

***

### Matching information of a trading pair

{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "match"
  ],
  "token": ""    # optional (JWT-token)
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "match"
  ],
  "token": ""    # optional (JWT-token)
}
```
{% endtab %}
{% endtabs %}

***

### Success order information of a trading pair

{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "trade"
  ],
  "token": ""    # required (JWT-token) 
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "trade"
  ],
  "token": ""    # required (JWT-token)
}
```
{% endtab %}
{% endtabs %}

***

### Order change infomation of a trading pair

{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "order"
  ],
  "token":""  # required (JWT-token)
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "product_ids": [
    "UNI-USDC"
  ],
  "channels": [
    "order"
  ],
  "token": ""  # required (JWT-token)
}
```
{% endtab %}
{% endtabs %}

***

### The asset change information of an account

{% tabs %}
{% tab title="Subscribe" %}
```
{
  "type": "subscribe",                                
  "currency_ids": [
    "UNI",
    "USDC"
  ],
  "channels": [
    "funds"
  ],
  "token": ""   # required (JWT-token)
}
```
{% endtab %}

{% tab title="Unsubscribe" %}
```
{
  "type": "unsubscribe",                                
  "currency_ids": [
    "UNI",
    "USDC"
  ],
  "channels": [
    "funds"
  ],
  "token":""   # required (JWT-token)
}
```
{% endtab %}
{% endtabs %}
