# Developers Onboarding

## Start Here 

**What is Cambiatus?**

Open online platform that enables communities/groups with environmental and social objectives to create and implement their own community currencies. 

At Cambiatus we make the blockchain technology available and user friendly, so these communities can take full advantage of it and solve their environmental or social problems. Cambiatus is also becoming a tool to make DAC (decentralized autonomous communities) creation easy and fun. 

**What is DAC?**

We have put together a document called the [Path to Knowledge](https://docs.google.com/document/d/1cKmTSR9VpPkYyD-uhpnnAuF4JITGWSu6X5BP9le1yMw/edit) in which we offer some sources of information which you can follow to learn about all the above topics. 

**Now what really means Cambiatus?**

In Spanish “Cambio” or "Cambiar" is the word used to express “Change”.  Cambiatus refers to a change in our mindset, a change in the way we understand money, organizations and collaboration. 

When people start using Cambiatus methodologies and tools, something changes inside them, they get it! 

# Welcome to Cambiatus!

As a new dev, you'll be working on a small, focused team of generalists. Even though you have an area where you shine, we love to see people that enjoys working on multiple parts of the app, as it gives you a bigger picture on how everything comes together!

Here you'll find instructions to stuff all devs do!

## Environments

We have 3 envs in Cambiatus: **Production**, **Demo** and **Staging**. All our apps default to staging, this way if you just cloned an app and runned it, beware that it will point to it. By "pointing", it means how it conects to other apps. For example, frontend by default pushes transactions to staging EOSIO, consumes from staging backend. Event Source by default tries to conect to staging EOSIO and writes to staging Postgres. 
This way it will be easy to start working, because you don't have to run all apps to start working on something!

This also means that Staging is prone to errors from time to time as its used by the whole development team, be sure to communicate your work so we all can coordinate!

## Architecture

Our app is composed of a few repos, that work together to deliver our final app. Here's an outline:

- [Frontend](https://github.com/cambiatus/frontend) -- Elm app, its the main interaction point for our users;
- [Backend](https://github.com/cambiatus/backend) -- Our API written in Elixir. It handles Postgres' Database migrations;
- Event Source -- Javascript app that listens to our EOSIO blockchain and copies its data to Postgres;
- Postgres -- Database where we copy the current state of the blockchain data, its easier to manipulate and consume;
- [EOSIO](https://github.com/cambiatus/contracts) -- Blockchain that holds the final state of our app, aside from the frontend, all apps just exist to consume its data more easily.

## Important Resources

- [GraphQL](graph_doc/graphql.md) wiki page
- [PostgreSQL](postgresql.md) wiki page

Have fun and hack away!!