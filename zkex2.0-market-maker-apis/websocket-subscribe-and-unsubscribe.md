# 🤍 Websocket Subscribe & Unsubscribe

### Order data of any trading pair (`level2`)

*   Subscribe

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
*   Unsubscribe

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
*   **Notice:**

    When you subscribe to [level2](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#ws-level2) for the first time, you will receive the snapshot data by [push-snapshot](https://github.com/ZKEX/dev-docs/tree/main/market-maker-apis#push-snapshot)

***

### K-line data of a trading pair (1/3/5/15/30/60min/2/4/6/12/24hour)

*   Subscribe

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
*   Unsubscribe

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
*   Channel name comparison table

    | channel name   | time   |
    | -------------- | ------ |
    | candles\_1m    | 1min   |
    | candles\_3m    | 3min   |
    | candles\_5m    | 5min   |
    | candles\_15m   | 15min  |
    | candles\_30m   | 30min  |
    | candles\_60m   | 60min  |
    | candles\_120m  | 2hour  |
    | candles\_240m  | 4hour  |
    | candles\_360m  | 6hour  |
    | candles\_720m  | 12hour |
    | candles\_1440m | 24hour |

***

### Ticker info of a trading pair

*   Subscribe

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
*   Unsubscribe

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

***

### Matching information of a trading pair

*   Subscribe

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
*   Unsubscribe

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

***

### Success order information of a trading pair

*   Subscribe

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
*   Unsubscribe

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

***

### Order change infomation of a trading pair

*   Subscribe

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
*   Unsubscribe

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

***

### The asset change information of an account

*   Subscribe

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
*   Unsubscribe

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
