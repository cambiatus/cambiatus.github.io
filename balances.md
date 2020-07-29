## Balances

In Cambiatus an user can participate on several different communities and have different amount on their balance for each of them.

We provide an endpoint for checking that, using EOSIO API:

```shell
curl -X "POST" "https://eosio.cambiatus.io/v1/chain/get_table_rows" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "code": "bes.token",
  "scope": "lucca",
  "json": true,
  "table": "accounts",
  "limit": 1000
}'
```

You can change the JSON param `scope` with the account you want to query.
