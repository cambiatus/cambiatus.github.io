# **GraphQL**

## **Sample Queries & Mutations**

Here are few sample queries to speed up your developing/testing process.
*Note: thanks for your patience as the platform is always evolving, there might outdated sample queries. Please let us know if you find a mistake and/or outdated information.*

1. profile
```graphql
{
  profile(input: {account: "lucca"}) {
    account
    avatar
    bio
    chatToken
    chatUserId
    createdAt
    createdBlock
    createdEosAccount
    email
    interests
    location
    name
  }
}
```
### **Mutations**

1. Sign-up
```graphql
mutation {
  signUp(input: {account: "someuser", email: "some@user.com", invitationId: "1", name: "Some User", publicKey: "mypublickey"}) {
    reason
    status
  }
}
```
2. UpsertKyc
```graphql
mutation {
  upsertKyc(input: {accountId: "someUser1", countryId: "1", document: "111111111", documentType: "cedula_de_identidad", phone: "44433333", userType: "natural"}) {
    document
    documentType
    isVerified
    phone
    userType
  }
}
```
2. UpsertAddress
```graphql
mutation {
  upsertAddress(input: {accountId: "someUser1", countryId: "1", neighborhoodId: "1", street: "Elm Street", number: "321", stateId: "1", cityId: "1", zip: "10102"}) {
    zip
  }
}
```
4. DeleteKyc
```graphql
mutation {
  deleteKyc(input: {accountId: "someUser1"}) {
    status
    reason
  }
}
```
5. DeleteAddress
```graphql
mutation {
  deleteAddress(input: {accountId: "someUser1"}) {
    status
    reason
  }
}
```