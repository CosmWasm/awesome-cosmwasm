# Awesome CosmWasm [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

Collection of awesome things related to
[CosmWasm smart contracts](https://www.cosmwasm.com).

Please read the [contribution guidelines](CONTRIBUTING.md) if you want to
contribute.

## Contents

- [General Resources](#general-resources)
- [CosmWasm Framework](#cosmwasm-framework)
- [Smart Contracts](#smart-contracts)
  - [`cw-plus` Specifications and Examples](#cw-plus-specifications-and-examples)
  - [Trivial Contracts](#trivial-contracts)
- [External Projects](#external-projects)
- [Tooling](#tooling)
- [dApps](#dapps)

## General Resources

- [CosmWasm official documentation](https://docs.cosmwasm.com)
- [CosmWasm framework](https://github.com/CosmWasm/cosmwasm) - a "core" CosmWasm
  repo. This includes the core Rust framework for writing a smart contract, a
  virtual machine that runs smart contracts and is embedded in any chain running
  them, the IDL format for describing the interface of a smart contract, and
  more! A few of these are commonly dependencies of smart contracts.
- [CosmWasm template](https://github.com/CosmWasm/cw-template) - a template for
  getting an empty smart contract up and running quickly. Instructions included!

## CosmWasm Framework

- [cosmwasm-std](https://crates.io/crates/cosmwasm-std)
  ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/std)): The
  standard library for building CosmWasm smart contracts. Code in this package
  is compiled into the smart contract.
- [cw-storage-plus](https://crates.io/crates/cw-storage-plus)
  ([repo](https://github.com/CosmWasm/cw-storage-plus)): Helper methods to
  reduce boilerplate for storing data types. Easier and more secure persistence
  layer.
- [cosmwasm-schema](https://crates.io/crates/cosmwasm-schema)
  ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/schema)): A
  dependency for CosmWasm contracts to generate the IDL (interface description)
  files. These are consumed e.g. by
  [`ts-codegen`](https://github.com/CosmWasm/ts-codegen) to automagically get a
  _TypeScript_ client for your contract.
- [cw-multi-test](https://crates.io/crates/cw-multi-test)
  ([repo](https://github.com/CosmWasm/cw-multi-test)):
- [cw-utils](https://crates.io/crates/cw-utils)
  ([repo](https://github.com/CosmWasm/cw-utils)): A collection of (somewhat
  random) helpers we found useful when developing `cw-plus` contracts and specs.
  Available as a library at crates.io!

## Smart Contracts

Before you create a PR to add your contract here, read the
[publishing guidelines](https://github.com/confio/cosmwasm-template/blob/master/Publishing.md)
and make sure you complete them all, specifically adding an OSI-approved license
and checking in valid artifacts for the build (`contract.wasm`,
`schema/*.json`).

We do validate the artifacts and perform a basic code review of contracts
included in this list. However, nothing terribly comprehensive and inclusion
here should not be taken in lieu of a proper audit. We do provide some
guidelines on
[sharing code reviews in a decentralized manner](https://github.com/confio/cosmwasm-template/blob/master/Importing.md)
which can be used as the basis for a peer-reviewed audit.

### `cw-plus` Specifications and Examples

[The `cw-plus` repo](https://github.com/CosmWasm/cosmwasm-plus) houses both
protocol specifications and their reference implementations. These
implementations are meant both as examples of production-ready contracts and
pieces you might like to use in your project as they are.

#### Specifications

- [cw1](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw1) -
  proxy contracts that are meant to forward a message (probably after checking
  the sender against some form of access control), this time with the contract
  as the sender.
- [cw2](https://github.com/CosmWasm/cw-plus/tree/main/packages/cw2) - contract
  metadata (name and version) that can be inspected directly, without querying
  the contract.
- [cw3](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md) -
  multisig and voting.
- [cw4](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md) -
  group membership management with weights.
- [cw20](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw20) -
  fungible token.

#### Reference implementations

- [cw1-whitelist](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-whitelist)
  by [ethanfrey](https://github.com/ethanfrey): This may be the simplest
  implementation of
  [cw1](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw1), a
  whitelist of addresses. It contains a set of admins that are defined upon
  creation. Any of those admins may Execute any message via the contract, per
  the [CW1](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw1)
  spec.
- [cw1-subkeys](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-subkeys)
  by [ethanfrey](https://github.com/ethanfrey): This builds on cw1-whitelist to
  provide the first non-trivial solution. It still works like cw1-whitelist with
  a set of admins (typically 1) which have full control of the account. However,
  you can then grant a number of accounts allowances to send native tokens from
  this account.
- [cw3-fixed-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw3-fixed-multisig):
  This is a simple implementation of the
  [cw3 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md).
  It is a multisig with a fixed set of addresses created upon initialization.
  Each address may have the same weight (K of N) or some may have extra voting
  power.
- [cw3-flex-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw3-flex-multisig):
  This builds on cw3-fixed-multisig with a more powerful implementation of the
  cw3 spec. It is a multisig contract that is backed by a
  [cw4](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw4)
  (group) contract, which independently maintains the voter set.
- [cw4-group](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw4-group):
  This is a basic implementation of the
  [cw4 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md).
  It fulfills all elements of the spec, including the raw query lookups, and it
  designed to be used as a backing storage for cw3 compliant contracts.
- [cw4-stake](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw4-stake):
  This is a second implementation of the
  [cw4 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md).
  It fufills all elements of the spec, including the raw query lookups, and it
  is designed to be used as a backing storage for cw3 compliant contracts.
- [cw20-base](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-base)
  by [ethanfrey](https://github.com/ethanfrey): Basic implementation of a
  [cw20](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw20)
  contract. It implements the
  [cw20](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw20/README.md)
  spec and is designed to be deloyed as is, or imported into other contracts to
  easily build cw20-compatible tokens with custom logic.

### Trivial Contracts

These contracts demonstrate best practices and learning references. Please do
not use them in production:

- [name service](https://github.com/InterWasm/cw-contracts/tree/main/contracts/nameservice):
  Blockchain name service in CosmWasm.
- [escrow](https://github.com/InterWasm/cw-contracts/tree/main/contracts/escrow):
  This is a simple single-use escrow contract.
- [simple-option](https://github.com/InterWasm/cw-contracts/tree/main/contracts/simple-option):
  This is a simple financial option contract.
- [voting](https://github.com/InterWasm/cw-contracts/tree/main/contracts/voting):
  This is a simple voting contract. It creates a contract to manage token
  weighted polls, where voters deposit native coins in order to vote. Voters can
  withdraw their stake, but not while a poll they've participated in is still in
  progress.
- [cw20-pot](https://github.com/InterWasm/cw-contracts/tree/main/contracts/cw20-pot) -
  Basic smart contract using cw20 contract

## External Projects

These projects/contracts are developed and maintained by CosmWasm community.

- [substrate-light-client](https://github.com/ChorusOne/substrate-light-client):
  Implementation of substrate light client in rust compilable to wasm. It is
  written to be integrated with CosmWasm readily, and is optimized to run in a
  constrained environment of a smart contract.
- [tendermint-light-client](https://github.com/ChorusOne/tendermint-light-client):
  Implementation of tendermint light client in rust compilable to wasm. The code
  is heavily inspired from tendermint-rs. It is optimized to run in a
  constrained environment of a smart contract.
- [CW20 Clawback](https://github.com/tomtau/hackatom): HackAtom V prototype of a
  "clawback" contract inspired by Bitcoin Vaults
- [NFT Marketplace](https://github.com/BlockscapeNetwork/hackatom_v/tree/master/contracts/marketplace):
  HackAtom V prototype of a CW721 "NFT Marketplace Smart Contract"

## Tooling

- [cosmwasm/rust-optimizer](https://github.com/CosmWasm/rust-optimizer) This is
  a Docker build with a locked set of dependencies to produce reproducible
  builds of cosmwasm smart contracts. It also does heavy optimization on the
  build size, using binary stripping and `wasm-opt`.

## dApps

You can find the Official Confio maintained dApp instances deployed here:
[https://dapps.cosmwasm.com](https://dapps.cosmwasm.com)

- Name service:
  [https://dapps.cosmwasm.com/names](https://dapps.cosmwasm.com/names)
- Native wallet:
  [https://dapps.cosmwasm.com/wallet](https://dapps.cosmwasm.com/wallet)
- CW20 wallet:
  [https://dapps.cosmwasm.com/cw20-wallet](https://dapps.cosmwasm.com/cw20-wallet)
- CW20 staking service:
  [https://dapps.cosmwasm.com/stakes](https://dapps.cosmwasm.com/stakes)

The code is in the packages directory of the monorepo:
[https://github.com/CosmWasm/dApps/tree/master/packages](https://github.com/CosmWasm/dApps/tree/master/packages)

- Name service:
  [https://github.com/CosmWasm/dApps/tree/master/packages/name-service](https://github.com/CosmWasm/dApps/tree/master/packages/name-service)
- Native wallet:
  [https://github.com/CosmWasm/dApps/tree/master/packages/wallet](https://github.com/CosmWasm/dApps/tree/master/packages/wallet)
- CW20 wallet:
  [https://github.com/CosmWasm/dApps/tree/master/packages/cw20-wallet](https://github.com/CosmWasm/dApps/tree/master/packages/cw20-wallet)
- CW20 staking service:
  [https://github.com/CosmWasm/dApps/tree/master/packages/staking-service](https://github.com/CosmWasm/dApps/tree/master/packages/staking-service)
