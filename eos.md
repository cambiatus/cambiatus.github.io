# EOS

## Blockchain Concepts

Cambiatus is a [Dapp](https://en.wikipedia.org/wiki/Decentralized_application) and as any Dapp it has certain concepts that are important to understand.

### Blockchain is just a database

Blockchains are just databases with some characteristics. We will basically focus on a few:

1. How to read data on a blockchain
2. How to write data on a blockchain

### How to read data

Blockchains, as other databases allows you to read data from it. Different blockchains have different ways. In Cambiatus we use the [EOS Blockchain](https://eos.io) which is a blockchain that allow for Smart Contracts, which in a way are just a way to describle different tables and actions. Tables being how the data is structured and actions being the ways on which we can modify that data (this is, of course, a simplification)

On EOS you can read data by doing HTTP calls. Those are very simple requests and Cambiatus offers a more streamlined and capable GraphQL API for querying data. You can check it out on our [API Documentation](/api/index.md)

### How to write data on a blockchain

All writes on blockchain apps must be authenticated. On regular apps you usually have a username and password in order to write autenticated information.
But in blockchain you must create a transaction, and sign it.

#### Transactions

Transactions are the basic way for you to update the blockchain. Transactions basically contains two fields: `actions` and a `signature`.

Actions is a JSON array containing changes you want to do. Lets grab a simple example of the Cambiatus' `Transfer` action:

```json
{
    "compression": "none",
    "transaction": {
        "expiration": "2020-07-21T01:51:40",
        "ref_block_num": 37288,
        "ref_block_prefix": 3703959568,
        "max_net_usage_words": 0,
        "max_cpu_usage_ms": 0,
        "delay_sec": 0,
        "context_free_actions": [],
        "actions": [
            {
                "account": "bes.token",
                "name": "transfer",
                "authorization": [
                    {
                        "actor": "lucca",
                        "permission": "active"
                    }
                ],
                "data": "000000000083908e80cc8e0e9b24cd760100000000000000004245530000000000"
            }
        ],
        "transaction_extensions": []
    },
    "signatures": [
        "SIG_K1_KfWMpxaQwHTSeCvEJWzBSRsptcMdAVUrR7DGw4rERExxMuSoQyonWhEV8US6hjRdH2hQpLUqqqgQSCfu4j1t3U3ZbhoVC6"
    ]
}
```

The import bit is:

```json
{
   "account": "bes.token",
   "name": "transfer",
   "authorization": [
     {
       "actor": "lucca",
       "permission": "active"
     }
   ],
   "data": "000000000083908e80cc8e0e9b24cd760100000000000000004245530000000000"
 }
```
- **Account**: Is the contract address. For all transactions on Cambiatus you'll need to call `bes.token` or `bes.cmm`, depending on what you want to do.
- **Name**: Is the action name, a contract has several different actions. You'll have to specify one.
- **Authorization**: It is the account that wants to send a transaction. _For example: If you want to transfer, you'll have to provide a `from` and a `to` params, and an authorization from the `from` account_
- **Data**: On the example it is encoded, but it's all the required params for transfer. You can check the required params for transfer [here](https://github.com/cambiatus/contracts/blob/master/bespiral.token/bespiral.token.hpp#L51)

#### Signatures

In order to sign, you'll need a private key that is associated to a valid EOS Account. We won't detail how to do it here, since its only conceptual but EOS has several signature providers, such as [eosjs](https://www.npmjs.com/package/eosjs) (javascript implementation) or [eos-sharp](https://github.com/GetScatter/eos-sharp)

With both an array of actions and a signature you'll be able to write to the blockchain
