<h1 align="center">
  <br>
  <a href="https://www.energyweb.org/"><img src="https://www.energyweb.org/wp-content/uploads/2019/04/logo-brand.png" alt="EnergyWeb" width="150"></a>
  <br>
  EnergyWeb Origin
  <br>
  <br>
</h1>

**Zero** is a set of toolkits that together provide a system for issuance and management of Energy Attribute Certificates (EACs). This repository is an entry point to Origin systems. It has a goal of explaining briefly the whole system and providing you with insight and info where to explore next.

<p align="center">
  <img src="https://github.com/energywebfoundation/zero/actions/workflows/deploy-master.yml/badge.svg" />
</p>

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Packages](#packages)
  - [Applications, Infrastructure and Demo](#applications-infrastructure-and-demo)
  - [Packages types](#packages-types)
    - [Stable](#stable)
    - [Canary](#canary)
    - [Preview](#preview)
- [Installation](#installation)
- [Build](#build)
- [Test](#test)
- [Run demo](#run-demo)
  - [Preparation](#preparation)
  - [Running](#running)
  - [Heroku environment provisioning](#heroku-environment-provisioning)
- [Energy Attribute Certificates](#energy-attribute-certificates)
- [Key modules and components](#key-modules-and-components)
  - [Key repositories](#key-repositories)
  - [Other components](#other-components)
- [Deployment](#deployment)
- [Contribution guidelines](#contribution-guidelines)

## Packages

### Applications, Infrastructure and Demo

| Package                                                   | Description                                |
| --------------------------------------------------------- | ------------------------------------------ |
| [`@energyweb/zero-ui`](/packages/zero-ui)             | UI for Zero project |
| [`@energyweb/zero-api`](/packages/zero-api) | Zero API |

### Packages types

Zero monorepo produce 3 types of the packages that are meant to be used in different use-cases:

#### Stable

Stable  packages are created during `release` branch build.

Install using `yarn add @energyweb/{package}`

#### Canary

Canary packages are created during `master` branch builds. Canary reflects current state of the `master` branch, they should be a working versions considers as `alpha`

Install using `yarn add @energyweb/{package}@canary`

#### Preview

Preview packages are built on a special `preview` branch, this is mostly used as internal tool for tests, demos, discussions.

Install using `yarn add @energyweb/{package}@preview`

## Installation

Make sure have latest `yarn` package manager installed.

```shell
yarn
```

## Build

```shell
yarn build
```

## Test

```shell
yarn test
```

## Run demo

### Preparation

0. Make sure you are using Node 14.x.x
1. Install [Postgres](https://www.postgresql.org/download/) 12.x+ and create a new database named `zero`.

We recommend using Docker based setup as follows (requires psql command line tool installed):

```
docker pull postgres
docker run --name zero-postgres -e POSTGRES_PASSWORD=postgres -d -p 5432:5432 postgres
psql -h localhost -p 5432 -U postgres -c "CREATE DATABASE zero"
```

2. Make sure you have created a `.env` file in the root of the monorepo and that all necessary variables are set.
   Use [`.env.example`](.env.example) as an example of how the `.env` file should look.


### Running


```shell
yarn start
```

Visit the UI at: http://localhost:3000.

## Key modules and components

Overview of architecture

### Key repositories

This section lists key entry points to start your journey with Zero.

2. [ew-zero-backend](https://github.com/energywebfoundation/zero/tree/master/apps/ew-zero-api) - This repository is used to act as a backend service for off-chain data storage.
3. [ew-zero-frontend](https://github.com/energywebfoundation/zero/tree/master/apps/ew-zero) - frontend of the system needed to view data stored in smart contracts (on-chain) and in the backend (off-chain). To interact with the Origin frontend you'll need [MetaMask](https://metamask.io).

### Other components

TBD

## Deployment

For deployment instructions please refer to [Deployment](https://github.com/energywebfoundation/zero/wiki/Zero-Deployment) wiki page.

## Contribution guidelines

If you want to contribute to Zero, be sure to follow classic open source contribution guidelines (described below).

1. Commiting a change
    - Fork the repository
    - Make a change to repo code
    - Commit the change to the `master` branch
2. Pull request
    - Open a pull request from your fork `master` branch
    - Request code reviews from [@arkadiuszsz](https://github.com/Kuzirashi),  [@kosecki123](https://github.com/kosecki123)
    - Once the PR is approved and the build passes, it will be merged to the master branch
