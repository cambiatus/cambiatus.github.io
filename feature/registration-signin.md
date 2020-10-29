# Registration and Sign In

Although Cambiatus uses EOS, we have a Sign Up/Sign In process that is a little different from other blockchain apps. First of all we try to abstract public and private key pairs from the user.

## Basic registration steps

If the user isn't trying to register from an Invitation, we use the basic registration process. It all begins by the user clicking on `Don't have an account yet? Create now` on the Login page. From there the user will be take to the registration page, where he/she will have to fill in 3 infos: Full name, account name (which is an [EOS account](integration/accounts.html)) and an email address. 

The frontend will generate this request:

```graphql
mutation {
  signUp3423593742: signUp(input: 
    {
      account: "minminminbb4", 
      email: "a@a",
      name: "Test Min",
      publicKey: "EOS6ha8YSp5BHwHxmXW76M8zC7mCCRYNvbVw7Ja3grxDhYV6UKfjw"
    }) {
    status955176064: status
    reason3832528868: reason
  }
}
```

Now the backend will take over. Roughly the backend will do the following steps:

- Try to find if the `account` is already registred 
- Check if the `account` and `email` are valid
- Tries to create the account on EOS
- Creates the user in the DB
- [Netlinks](/features/networks.md) the newly created user to the community

All those steps are required to work properly in order for the signup to be completed. 
