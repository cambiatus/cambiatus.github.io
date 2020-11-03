# Welcome to Cambiatus!

As a new dev, you'll be working on a small, focused team of generalists. Even though you have an area where you shine, we love to see people that enjoys working on multiple parts of the app, as it gives you a bigger picture on how everything comes together!

Here you'll find instructions to stuff all devs do!

### Architecture

Our app is composed of a few repos, that work together to deliver our final app. Here's an outline:

- Frontend -- Elm app, its the main interaction point for our users;
- Backend -- Our API written in Elixir. It handles Postgres' Database migrations;
- Event Source -- Javascript app that listens to our EOSIO blockchain and copies its data to Postgres;
- Postgres -- Database where we copy the current state of the blockchain data, its easier to manipulate and consume;
- EOSIO -- Blockchain that holds the final state of our app, aside from the frontend, all apps just exist to consume its data more easily.


### Environments

We have 3 envs in Cambiatus: **Production**, **Demo** and **Staging**. All our apps default to staging, this way if you just cloned an app and runned it, beware that it will point to it. By "pointing", it means how it conects to other apps. For example, frontend by default pushes transactions to staging EOSIO, consumes from staging backend. Event Source by default tries to conect to staging EOSIO and writes to staging Postgres. 
This way it will be easy to start working, because you don't have to run all apps to start working on something!

This also means that Staging is prone to errors from time to time as its used by the whole development team, be sure to communicate your work so we all can coordinate!
