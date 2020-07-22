# Awesome CosmWasm [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

Collection of awesome things related to [CosmWasm smart contracts](https://www.cosmwasm.com).

Please read the [contribution guidelines](CONTRIBUTING.md) if you want to contribute.

## Contents

  - [General Resources](#general-resources)
  - [Smart Contracts](#smart-contracts)
  - [Smart Contract Libraries](#smart-contract-libraries)
  - [Tooling](#tooling)
  - [dApps](#dapps)

## General Resources

- [CosmWasm official documentation](https://docs.cosmwasm.com)
- [CosmWasm framework](https://github.com/CosmWasm/cosmwasm) - you will import this for your contracts, README has useful info and links
- [CosmWasm template](https://github.com/CosmWasm/cosmwasm-template) - how to start building your own contract

## Smart Contracts

Before you create a PR to add your contract here, read the [publishing guidelines](https://github.com/confio/cosmwasm-template/blob/master/Publishing.md) and make sure you complete them all, specifically adding an OSI-approved
license and checking in valid artifacts for the build (`contract.wasm`, `schema/*.json`).

We do validate the artifacts and perform a basic code review of contracts included in this list. However, nothing
terribly comprehensive and inclusion here should not be taken in lieu of a proper audit. We do provide some
guidelines on
[sharing code reviews in a decentralized manner](https://github.com/confio/cosmwasm-template/blob/master/Importing.md)
which can be used as the basis for a peer-reviewed audit.

### Plus Contracts

[The plus contracts](https://github.com/CosmWasm/cosmwasm-plus) are designed with a cosmwasm-specific spec and focus on composability.

- [cw1-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-multisig) by [ethanfrey](https://github.com/ethanfrey): This may be the simplest implementation of CW1, a "1 of N" multisig. It contains a set of admins that are defined upon creation. This is somewhat improved version of mask contract in the examples
- [cw20-base](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-base) by [ethanfrey](https://github.com/ethanfrey): Basic implementation of a cw20 contract. It implements the [CW20](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw20/README.md) spec and is designed to be deloyed as is, or imported into other contracts to easily build cw20-compatible tokens with custom logic.
- [cw20-escrow](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-escrow) by [ethanfrey](https://github.com/ethanfrey): Escrow meta-contract that allows multiple users to create independent escrows.

### Trivial Contracts

These contracts demonstrates best practices and learning references. Please do not use them in production:

- [mask](https://github.com/CosmWasm/cosmwasm-examples/tree/master/mask): The Mask works as a proxy contract that has an address and can hold tokens, and interact with other contracts like any normal user account. For more reading: [introducing the mask](https://medium.com/confio/introducing-the-mask-41d11e51bccf)
- [name service](https://github.com/CosmWasm/cosmwasm-examples/tree/master/nameservice): Blockchain name service in cosmwasm.
- [erc20](https://github.com/CosmWasm/cosmwasm-examples/tree/master/erc20): Implementation of Ethereum's [ERC20](https://eips.ethereum.org/EIPS/eip-20) interface.
- [escrow](https://github.com/CosmWasm/cosmwasm-examples/tree/master/escrow): This is a simple single-use escrow contract.

## External projects

These projects/contracts are developed and maintained by CosmWasm community.

- [substrate-light-client](https://github.com/ChorusOne/substrate-light-client): Implementation of substrate light client in rust compilable to wasm. It is written to be integrated with CosmWasm readily, and is optimized to run in a constrained environment of a smart contract.
- [tendermint-light-client](https://github.com/ChorusOne/tendermint-light-client): Implementation of tendermint light client in rust compilable to wasm. The code is heavily inspired from tendermint-rs. It is optimized to run in a constrained environment of a smart contract.
- [voting](https://github.com/levackt/cosmwasm-examples/tree/master/voting): This is a simple voting contract. It creates a contract to manage token weighted polls, where voters deposit native coins in order to vote.

## Smart Contract Libraries

- [cosmwasm-std](https://crates.io/crates/cosmwasm-std) ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/std)): The standard library for building CosmWasm smart contracts. Code in this package is compiled into the smart contract.
- [cosmwasm-storage](https://crates.io/crates/cosmwasm-storage) ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/storage)): Helper methods to reduce boilerplate for storing data types. Easier and more secure persistence layer.

## Tooling

- [cosmwasm/rust-optimizer](https://github.com/CosmWasm/rust-optimizer) This is a Docker build with a locked set of dependencies to produce reproducible builds of cosmwasm smart contracts. It also does heavy optimization on the build size, using binary stripping and `wasm-opt`.

## dApps

TODO
