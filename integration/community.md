## Introduction

In order to user Cambiatus, you'll need a community and users that belong to it.

### Creating a community

To create a community, you'll have to send a transaction with an action inside of it. Using EOSJS you can do the following:

```javascript
function createCommunity() {
   const authorization = 'devcambiatus@active'
   const data = {
    asset: '0 XXX',
    logo: '',
    name: 'Community Name',
    description: 'Some Description', // Max 256 chars
    inviterReward: '0 XXX',
    invitedReward: '0 XXX',
    hasObjectives: 0,
    hasShop: 0,
  }
  
  eos.contract('bes.cmm').then(cambiatus => {
    cambiatus.create(data, authorization).then(action => {
      // Do something after the creation
    }).catch(e => {
      console.error(e)
    })
  })
}
```


### Inviting users

We'll call call `netlink`: it will include the user to the network of the community

Please remember that you'll need to have a valid existing account. For learning how to create accounts checkout our [accounts page](accounts.md)

Here is an example in Javascript:

```javascript
function netlink() {
  const authorization = 'devcambiatus@active'
  const data = {
    cmm_asset: '0 XXX',
    new_user: '', // TODO: fill the new account here
    inviter: 'devcambiatus',
    skip_rewards: 1
  }

  eos.contract('bes.cmm').then(contract => {
    contract.netlink(data, authorization).then(action => {
      // Do something after inviting
    }).catch(e => {
      console.error(e)
    })
  })
}
```

For the authorization you will need to use this account: `devcambiatus@active`.


### Useful API Calls

We provide a [GraphQL](https://graphql.org) API for all Cambiatus entities. They are easy to explore and experiment with. For documentation on the API, [click here](https://api.cambiatus.io/api/graphiql)

Some examples of GraphQL queries you might find useful:

#### Get details on a community

```graphql
query {
  community(symbol: "BES") {
    name
    symbol
    hasShop
    hasObjectives
  }
}
```

#### Community members

```graphql
query {
  community(symbol: "BES") {
    name
    symbol
    hasShop
    hasObjectives
    members {
      name
    }
  }
}
```

#### Community Transfers (paginated to first 10)

```graphql
query {
  community(symbol: "BES") {
    name
    transfers(first: 10) {
      edges {
        node {
          fromId
          toId
          amount
          
        }
      }
    }
  }
}
```

