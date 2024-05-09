# ❓ What is ZKEX?

Offering bridgeless multi-chain trading secured with zero-knowledge, ZKEX is a trust-minimised and self-custodial order book DEX with CeFi performance.

Users are able to trade assets across multiple chains with a similar experience as on Binance or Coinbase, but instead, ZKEX is decentralized and non-custodial, with transactions secured with zero-knowledge proofs.

The exchange runs on a customised L3 app-rollup that aggregates liquidity from a number of EVM-compatible chains and L2 rollups.

ZKEX is built upon pioneering blockchain infrastructure from zkLink, LayerZero, Polyhedra, and Pyth Network.

{% hint style="info" %}
Note: the ZKEX exchange is now live. These Docs give a conceptual overview of the platform, and will be updated on a regular basis.
{% endhint %}

Official channels:

* Website: [https://zkex.com](https://zkex.com/)
* Twitter/X: [https://twitter.com/ZKEX\_Official](https://twitter.com/ZKEX\_Official)
* Telegram: [https://t.me/ZKEX\_Official](https://t.me/ZKEX\_Official)
* Discord: [https://discord.com/invite/zkex](https://discord.com/invite/zkex)
* Blog: [https://zkex.medium.com](https://zkex.medium.com/)
* Newsletter: [https://zkex.substack.com](https://zkex.substack.com)

## Why use ZKEX instead of another DEX?

A decentralized exchange (DEX) is a trading marketplace that allows secure peer to peer trading without any overseeing authority or custody of assets. An algorithm (in the form of code in a self-executing smart contract), rather than a middle party, checks to make sure both the buyer and seller complete their side of the trade on the platform.

Crypto traders on other DEXs often encounter volatile liquidity, high slippage costs, unpredictable gas fees, and limited functionality while stuck on a single chain.

> #### High costs and fees
>
> * Gas fees: Some DEX protocols run inefficient smart contracts to oversee transactions, resulting in high gas fees, especially for multi step processes.
> * Lack of micro-transactions: Due to gas fees, orders need to be above a certain value for transactions to be efficient.

> #### Losses on Automated Market Maker (AMM) exchanges:
>
> * Impermanent Loss: When assets inside a liquidity pool change in value, it often creates a discrepancy in asset prices. AMM liquidity pools rebalance the value of the assets, but this often causes a net loss in value for people contributing assets to the liquidity pool.
> * Slippage: If the price of a token you are trading changes while you are in the process of purchasing it, you would get a different rate than you intended. This may happen because of limited liquidity in an AMM that dynamically changes the value of the tokens as a supply of one is depleted. Alternatively, this could be caused by the token changing in value in the time it takes the transaction to be confirmed.
> * Maximal Extractable Value (MEV): The majority of MEV is conducted as hidden arbitrage in the form of Front/Back running and Sandwich attacks. Bad actors can extract profits by changing the order of transactions in a block, or inserting their own trades to push up or down prices.

> #### Limited functionality:
>
> * Isolated blockchains: If someone has USDC on the ETH-20 network, but would like to trade on another chain, they can’t make the trade directly. Instead they would need to bridge their funds over using a separate service, which can be tedious, subject to extra fees, and potentially unsafe.
> * Fewer trading strategies: Limit orders are often missing from most DEXs, which prevents automated trading.

## Core Concepts

Learning a few basic technical terms will help you understand crypto and web3 a little better. Here are some common concepts that you might come across when trading on ZKEX:

> #### L1 Networks
>
> A Layer1 (L1) network is the underlying blockchain infrastructure. They are self-contained ecosystems that handle transactions, security, consensus, and data availability - for this reason trading on L1 is known as being ‘on-chain’.
>
> For example, Ethereum or Solana are both L1 protocols, with their own different advantages.

> #### L2 Networks
>
> A Layer2 (L2) network is a network built on top of one of more L1 blockchains. They rely on the underlying L1 network for security and data availability, but process transactions at higher scale on separate infrastructure - for this reason trading on L2 is known as being ‘off-chain’.
>
> There are many types of L2 networks, with zero-knowledge rollups considered to be one of the most promising for enhanced scalability, privacy, and security.

> **L3 Networks**
>
> A Layer3 (L3) network is a third blockchain layer built on top of one of more L2 networks. The primary goal of an L3 network is to provide additional specialization and efficiency for specific use cases  or to enable new functionalities that are not feasible directly on L2 due to constraints like standardization, privacy requirements, or interoperability issues.

> #### Zero-knowledge Rollups
>
> A zero-knowledge rollup (ZK-rollup) is a way of using mathematics to verify the outcome of a transaction, and compress transaction data down to a minimum. A proof is generated, which is double-checked for judgement, after which the trade is confirmed as being successful, and written to the underlying L1 blockchain.
>
> The advantages of this method are that it enables higher scalability (and lower gas fees), fast finality, and a high level guarantee that the transaction has not been faked or tampered with.
>
> You can read more about ZK-Rollups in the [**Security**](https://github.com/ZKEX/docs/blob/master/docs/Concepts/Security) section.

> #### Order Book Matching Engine
>
> A central limit order book (CLOB) is essentially a meeting place for buyers and sellers to be matched together to fulfil their trades. ZKEX’s order book works in a similar way to a centralised order book exchange, however the the execution of the matched orders is decentralized and trustless.
>
> You can read more about order books in the [**Trading**](https://github.com/ZKEX/docs/blob/master/docs/Concepts/Trading) section.
