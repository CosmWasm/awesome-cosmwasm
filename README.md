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

- [CosmWasm official documentation](https://www.cosmwasm.com)
- [CosmWasm framework](https://github.com/confio/cosmwasm) - you will import this for your contracts, README has useful info and links
- [CosmWasm template](https://github.com/confio/cosmwasm-template) - how to start building your own contract

## Smart Contracts

Before you create a PR to add your contract here, read the [publishing guidelines](https://github.com/confio/cosmwasm-template/blob/master/Publishing.md) and make sure you complete them all, specifically adding an OSI-approved
license and checking in valid artifacts for the build (`contract.wasm`, `schema/*.json`).

We do validate the artifacts and perform a basic code review of contracts included in this list. However, nothing
terribly comprehensive and inclusion here should not be taken in lieu of a proper audit. We do provide some
guidelines on
[sharing code reviews in a decentralized manner](https://github.com/confio/cosmwasm-template/blob/master/Importing.md)
which can be used as the basis for a peer-reviewed audit.

- [cw-escrow](https://crates.io/crates/cw-escrow) by [ethanfrey](https://github.com/ethanfrey) ([repo](https://github.com/confio/cosmwasm-examples/tree/master/escrow)): A simple CosmWasm contract for an escrow with arbiter and timeout
- [cw-erc20](https://crates.io/crates/cw-erc20) by [webmaster128](https://github.com/webmaster128) ([repo](https://github.com/confio/cosmwasm-examples/tree/master/erc20)): Porting the erc20 token standard to CosmWasm

## Smart Contract Libraries

- [cw-storage](https://crates.io/crates/cw-storage) by [ethanfrey](https://github.com/ethanfrey) ([repo](https://github.com/confio/cosmwasm-examples/tree/master/escrow)): Helper methods to reduce boilerplate for storing data types. Easier and more secure persistence layer.

## Tooling

- [cosmwasm-opt](https://github.com/confio/cosmwasm-opt) is a build system for deterministic wasm code, essential so we can validate the rust code behind the byte code

## dApps

TODO
