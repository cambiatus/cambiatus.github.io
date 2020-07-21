## Cambiatus Accounts

Cambiatus accounts are EOS accounts. In order to create a new user you'll need to create a new Private Key (and store it safely) and a new Account

### Private Key generation

On EOS, the blockchain Cambiatus works on, we have the concept of account, that is, a readable 12 character name that identifies an user. That account have a key associated with it.

Our servers will create the account for the pulpero, but not the key. That should be on control of the users and should always be stored on a secure enclave. We recommend you follow the BIP-39 pattern. That pattern is very common in the crypto space and allows the user to store their private key as a 12 english word phrase. You can find instructions and sources for that in [here](https://www.notion.so/Creating-EOS-BIP39-compatible-Wallets-184f2ad79d9245e29770747e67f826d7) or [here](https://github.com/particl/genesis-wallet-generator). With those words, encoded in Hex, you can create a EOS `private key` and `public key`.

Store the `private key` and allow the user to see their public key.

---

### Creating a new account

You can do it by calling the following endpoint:

```shell
curl -X "POST" "<https://api.cambiatus.io/api/chain/account>" \\\\
     -H 'Content-Type: application/json; charset=utf-8' \\\\
     -d $'{
  "account": "testertester",
  "activeKey": "EOS5bxc8nWuk3KcDH7mnLERpyL9PT1tcv26tvD4VJg8KHazVVzzMv",
  "ownerKey": "EOS5bxc8nWuk3KcDH7mnLERpyL9PT1tcv26tvD4VJg8KHazVVzzMv"
}'
```

Here is the Ruby implementation if it makes it any easier for you:

```ruby
require 'net/http'
require 'json'

# Create account (POST)
def send_request
  uri = URI('<https://api.cambiatus.io/api/chain/account>')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  dict = {
            "account" => "testertester",
            "activeKey" => "EOS5bxc8nWuk3KcDH7mnLERpyL9PT1tcv26tvD4VJg8KHazVVzzMv",
            "ownerKey" => "EOS5bxc8nWuk3KcDH7mnLERpyL9PT1tcv26tvD4VJg8KHazVVzzMv"
        }
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Post.new(uri)
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

Remember that the account name must have 12 characters long and allow only downcase letters from a-z and numbers 1-5:

Valid account names:

- `entrepulpero`
- `testertester`
- `julienlucca1`
- `paualvarez51`
- `josuevillagr`

Invalid account names:

- `entrepulperos`
- `TesterTester`
- `julienlucca9`
- `paualvarez61`
- `josuevillagra`

Both `activeKey` and `ownerKey` must be generated the way we've talked before.

You can check if that account was in fact created by running this request:

```
curl -X "POST" "<https://eosio.cambiatus.io/v1/chain/get_account>" \\
     -H 'Content-Type: application/json; charset=utf-8' \\
     -d $'{
  "account_name": "fundes111111"
}'
```
