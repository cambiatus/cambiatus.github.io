# **GraphQL**

## **Sample Queries & Mutations**

Here are few sample queries to speed up your developing/testing process.
*Note: thanks for your patience as the platform is always evolving, there might outdated sample queries. Please let us know if you find a mistake and/or outdated information.*

1. profile
```
query {
		profile(
      input:
      { account: "someuser" })
  {
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
   invitations
   location
   name
  }
}
```
### **Mutations**

1. Sign-up
```
mutation {
		signUp (
    input: 
    { 
      account: "someuser",
	  email: "some@user.com",
      invitationId: "1",
      name: "Some User",
      publicKey: "mypublickey"
    })
  {
    reason
    status
  }
}
```
2. UpsertKyc
```
mutation {
		upsertKyc(
    input: 
    { accountId: "victorgdev12",
		countryId: "1",
      document: "111111111",
      documentType: "cedula_de_identidad",
      phone: "44433333",
      userType: "natural"
    })
  {
    document
    documentType
    isVerified
    phone
    userType
  }
}
```
2. UpsertAddress
```
mutation {
		upsertAddress(
    input: 
    { accountId: "andreymiskov",
    countryId: "1",
    neighborhoodId: "1",
    street: "Elm Street",
    number: "321",
    stateId: "1",
    cityId: "1",
    zip: "10102"
    })
  {
    zip
  }
}
```
4. DeleteKyc
```
mutation {
		deleteKyc(
    input: 
    { accountId: "victorgdev12" })
  {
   status
   reason
  }
}
```
5. DeleteAddress
```
mutation {
		deleteAddress(
    input: 
    { accountId: "victorgdev12" })
  {
   status
   reason
  }
}
```