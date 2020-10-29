# Networks

In Cambiatus, users can belong to multiple Communities. We keep track of who invited who in order to get a better grasp on the [Social Physics](https://en.wikipedia.org/wiki/Social_physics) of our communities. 

Its described by our `network` table that can [be seemed here](https://local.bloks.io/account/cambiatus.cm?nodeUrl=demo.cambiatus.io&coreSymbol=SYS&systemDomain=eosio&loadContract=true&tab=Tables&account=cambiatus.cm&scope=cambiatus.cm&limit=100&table=network)

We allow all users to invite their friends over to the community using their an invitation link, that they can generate on their dashboard. Here is an example: https://demo.cambiatus.io/invite/3WR3wl

Developers can also add an [account](/integration/accounts.md) to the network programatically using our API, by calling the action `netlink`

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
      // TODO: Do something after the user had been successfully invited
    }).catch(e => {
      console.error(e)
    })
  })
}
```
