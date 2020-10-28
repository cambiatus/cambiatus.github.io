## Introduction

In order to user Cambiatus, you'll need a community and users that belong to it.

### Creating a community

To create a community, you'll have to use our frontend. You can always use https://demo.cambiatus.io/community/new to create communities and test your work. Just keep in mind that we periodically reset all the data on that env, as its not proper for production usage, so don't get to attached to your data. 

### Inviting users

All new users must be added to the community network. We can do so by calling the `netlink` action.

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

  eos.contract('cambiatus.cm').then(contract => {
    contract.netlink(data, authorization).then(action => {
      // Do something after inviting
    }).catch(e => {
      console.error(e)
    })
  })
}
```

For the authorization, remember you'll have to use an account that belongs to the community you specified. 


### Useful API Calls

We provide a [GraphQL](https://graphql.org) API for all Cambiatus entities. They are easy to explore and experiment with. For documentation on the API, [click here](https://demo.cambiatus.io/api/graphiql)

Some examples of GraphQL queries you might find useful:

#### Get details on a community

```graphql
query {
  community(symbol: "CMB") {
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
  community(symbol: "CMB") {
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
  community(symbol: "CMB") {
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

