---
description: FeeThere is no charge or fee to activate your L2 account on ZKEX.
---

# 🔐 Security

{% hint style="info" %}
'Security by design' is one of the guiding principles at ZKEX.

Security is implemented at every level: the wallet, deposits, withdrawals, computations and consensus of transactions.

By removing token bridges, mathematically verifying transactions, and implementing multiple fail safes, the danger of malicious behaviour done by anyone (including the ZKEX team) is virtually eliminated.

Transactions are mathematically verified to ensure every trade completes as expected, or is rejected.
{% endhint %}

## Wallet

When you connect your browser wallet to ZKEX and 'deposit' funds into ZKEX for trading, your assets are temporarily 'locked' in your browser wallet, and only moved when a transaction is successfully completed.

This ensures you retain custody in your own wallet, and there are no assets on ZKEX to attack.

## Deposits

Moving your assets to trade on ZKEX is safe and secure, as no bridges are involved.

Instead, an L2 network is built natively on top of each connected blockchain, which makes it quick and easy to 'move' assets into ZKEX to trade from your browser wallet.

## Transactions

ZKEX applies a two-step security guarantee of verification + judgment.

> #### Applying ZK-Proofs
>
> Zero Knowledge is a branch of cryptography that uses mathematics to calculate something called a 'zero-knowledge proof' (ZK-Proof) - which is like 'a seal of approval' to check if a given statement is true.
>
> When applying ZK-proofs to cryptocurrency trading, a proof is generated from the transaction data using an algorithm. This ZK-Proof is a one-way calculation of the transaction, that cannot be reverse engineered to reveal the details of that transaction or any details of the people involved.
>
> This proof can be sent to a 'verifier', who checks that the proof is correct using another special algorithm.

> #### Step 1: Verification
>
> In the case of a multi-chain transaction (say from Ethereum to Avalanche), there are assets moving between two different blockchains, so we actually have two ZK-Proofs. By further calculating these two ZK-Proofs together, we create something called a ‘ZK-recursive-proof’.
>
> In the end, we have one single calculation to verify the entire multi-chain transaction. This single ‘ZK-recursive-proof’ can be verified if transactions happened and completed successfully — and if so, can be published on both blockchains.

> #### Step 2: Judgement
>
> To double-check the verification was correct, an independent network of juries (that is on LayerZero) judges the consistency of the two generated 'ZK-proofs' sent to each connected blockchain.
>
> This additional check by an independent third-party gives peace of mind and guarantees consistency, while keeping the details of the trade completely private.

## Disaster recovery

ZKEX allows an emergency withdrawal function - giving users the ability to unlock their assets in case of an extreme situation.

Details of how to do this will be released soon on the [**L2Wallet**](https://github.com/ZKEX/docs/blob/master/docs/Concepts/L2Wallet) page.

## Technical details

For more technical information about our security stack, please see:

* [https://docs.zk.link/docs/Technology/About-Security](https://docs.zk.link/docs/Technology/About-Security)
* [https://docs.zksync.io/userdocs/security/](https://docs.zksync.io/userdocs/security/)
* [https://layerzero.network/pdf/LayerZero\_Whitepaper\_Release.pdf](https://layerzero.network/pdf/LayerZero\_Whitepaper\_Release.pdf)

## Security audits

A security audit is currently under way and will be published on our website.

In future, a security review will be conducted before every update.

## Bug Bounty Program

After launch, we will offer a bug bounty program, with generous rewards to participants.

## Decentralization

During the development phase, ZKEX is operating as non-custodial, centrally operated entity. As the project progresses, we will further decentralise all parts of our infrastructure and organization.

