## Introduction

In order to user Cambiatus, you'll need a community and users that belong to it.

### Creating a community

### Inviting users

We'll call call `netlink`: it will include the user to the network of the community

Please remember that you'll need to have a valid existing account. For learning how to create accounts checkout our [accounts page](accounts.md)

Here is an example in Javascript:

```javascript
function netlink() {
  const authorization = 'fundes111111@active'
  const data = {
    cmm_asset: '0 PUL',
    new_user: '', // TODO: fill the new account here
    inviter: 'devcambiatus',
    skip_rewards: 1
  }

  eos.contract('bes.cmm').then(contract => {
    contract.netlink(data, authorization).then(action => {
      app.ports.netlinkSucceed.send(action.transaction_id)
    }).catch(e => {
      console.error(e)
      app.ports.netlinkFailed.send(e)
    })
  })
}
```

For the authorization you will need to use this account: `devcambiatus@active`.


### Useful API Calls
