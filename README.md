# Awesome CosmWasm [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

Collection of awesome things related to
[CosmWasm smart contracts](https://www.cosmwasm.com).

Please read the [contribution guidelines](CONTRIBUTING.md) if you want to
contribute.

## Contents

- [General Resources](#general-resources)
- [CosmWasm Framework](#cosmwasm-framework)
- [Smart Contract Libraries](#smart-contract-libraries)
- [Smart Contracts](#smart-contracts)
  - [`cw-plus` Specifications and Examples](#cw-plus-specifications-and-examples)
  - [Other Contracts](#other-contracts)
- [External Projects](#external-projects)
- [Tooling](#tooling)
- [dApps](#dapps)

## General Resources

- [The CosmWasm book](https://book.cosmwasm.com/) - A step-by-step guide to writing CosmWasm smart contracts.
- [CosmWasm framework](https://github.com/CosmWasm/cosmwasm) - The main CosmWasm repo, includes the core Rust framework for writing a smart contract and a virtual machine that runs smart contracts.
- [CosmWasm template](https://github.com/CosmWasm/cw-template) - A template for getting an empty smart contract up and running quickly with instructions.

## CosmWasm Framework

- [cosmwasm-std](https://github.com/CosmWasm/cosmwasm/tree/master/packages/std) - The standard library for writing and building CosmWasm smart contracts. [![cosmwasm-std on crates.io](https://img.shields.io/crates/v/cosmwasm-std.svg)](https://crates.io/crates/cosmwasm-std)
- [cw-storage-plus](https://github.com/CosmWasm/cw-storage-plus) - Helper methods to reduce boilerplate for storing data types for an easier and more secure persistence layer. [![cw-storage-plus on crates.io](https://img.shields.io/crates/v/cw-storage-plus.svg)](https://crates.io/crates/cw-storage-plus)
- [cosmwasm-schema](https://github.com/CosmWasm/cosmwasm/tree/master/packages/schema) - A dependency for CosmWasm contracts to generate the IDL (interface description) files. These are consumed e.g. by `ts-codegen` to automagically get a _TypeScript_ client for your contract. [![cosmwasm-schema on crates.io](https://img.shields.io/crates/v/cosmwasm-schema.svg)](https://crates.io/crates/cosmwasm-schema)
- [cw-multi-test](https://github.com/CosmWasm/cw-multi-test) - Test helpers for multi-contract interactions. [![cw-multi-test on crates.io](https://img.shields.io/crates/v/cw-multi-test.svg)](https://crates.io/crates/cw-multi-test)

## Smart Contract Libraries

- [cw-utils](https://github.com/CosmWasm/cw-utils) - A collection of helpers we found useful when developing `cw-plus` contracts and specs. [![cw-utils on crates.io](https://img.shields.io/crates/v/cw-utils.svg)](https://crates.io/crates/cw-utils)
- [cw-coins](https://github.com/steak-enjoyers/cw-plus-plus/tree/main/packages/coins) - A helper for managing multiple coins in a smart contract. [![cw-coins on crates.io](https://img.shields.io/crates/v/cw-coins.svg)](https://crates.io/crates/cw-coins)
- [cw-item-set](https://github.com/steak-enjoyers/cw-plus-plus/tree/main/packages/item-set) - A `HashSet` equivalent (set of unique items) that can be stored in smart contract storage. [![cw-item-set on crates.io](https://img.shields.io/crates/v/cw-item-set.svg)](https://crates.io/crates/cw-item-set)

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

- [cw1](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw1) - Proxy contracts that are meant to forward a message, with the contract as the sender by default.
- [cw2](https://github.com/CosmWasm/cw-plus/tree/main/packages/cw2) - Specification for migrating or inspecting smart contract metadata such as the name and the version without querying the contract.
- [cw3](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw3/README.md) - Voting and multisig contract.
- [cw4](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md) - Group membership management contract with weights.
- [cw20](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw20) - Fungible token loosely based on Ethereum's ERC20 standard with additional changes.

#### Reference implementations


- [cw1-whitelist](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-whitelist) - A simple implementation of cw1 specification using a whitelist of addresses for admins that are defined upon creation. It contains a set of admins that are defined upon creation.
- [cw1-subkeys](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-subkeys) - A similar implementation of cw-1 whitelist. However, subkeys allow admins to grant a number of accounts allowances for them to transfer native tokens.
- [cw3-fixed-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw3-fixed-multisig) - A simple implementation of the cw3 specification using multisig with a fixed set of addresses created upon initialization. Each address may have the same weight (K of N) or some may have extra voting power.
- [cw3-flex-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw3-flex-multisig) - A more advanced implementation of the cw-fixed-mulsitig backed by [cw4](https://github.com/CosmWasm/cosmwasm-plus/tree/master/packages/cw4), which independently maintains the voter set.
- [cw4-group](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw4-group) - A simple implementation of the cw4 spec fulfilling all elements of the spec, including raw query lookups, and it is designed to be used as backing storage for cw3 compliant contracts.
- [cw4-stake](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw4-stake) - An alternative cw4-group implementation that membership and weight are based on the staked token amount.
- [cw20-base](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-base) - A simple implementation of a cw20 contract. Can be deployed as is, or imported into other contracts to easily build cw20-compatible tokens with custom logic.

cw-1 whitelist, cw-1 subkeys, and cw-20 base are implemented by [ethanfrey](https://github.com/ethanfrey)

### Other Contracts

These contracts demonstrate best practices and learning references. Please do
not use them in production as is. You are welcome to fork them, and
independently review, refine and audit them, using them as a basis for your
protocol. Or just as inspiration

- [cw-tokens](https://github.com/CosmWasm/cw-tokens) - A collection with different variations of cw20 contracts.
- [cw-nfts](https://github.com/CosmWasm/cw-nfts) - The official repository for all work on NFT standards and reference contracts. This is where the [`cw721 spec`](https://github.com/CosmWasm/cw-nfts/tree/main/packages/cw721) lives.

## External Projects

These projects/contracts are developed and maintained by the CosmWasm community.

- [DA0-DA0/dao-contracts](https://github.com/DA0-DA0/dao-contracts) - DAO DAO is the leading software to build your own DAO on CosmWasm chains, quickly surpassing Aragon in functionality.
- [mars-protocol/v1-core](https://github.com/mars-protocol/v1-core) - Delphi's "Mars Protocol" is the leading lending protocol on Terra and soon launching on Osmosis.
- [public-awesome/launchpad](https://github.com/public-awesome/launchpad) - Stargaze provides contracts to easily create and manage new NFT collections.

## Tooling

- [cosmwasm/rust-optimizer](https://github.com/CosmWasm/rust-optimizer) - This is a Docker build with a locked set of dependencies to produce reproducible builds of cosmwasm smart contracts. It also does heavy optimization on the build size, using binary stripping and `wasm-opt`.
- [cosmology-tech/create-cosmos-app](https://github.com/cosmology-tech/create-cosmos-app) - Set up a modern Cosmos app with one command, ready to be iterated on.
- [mandrean/cw-optimizoor](https://github.com/mandrean/cw-optimizoor) - A very fast alternative to `rust-optimizer` for local development and testing. Written in Rust, with no dependency on Docker.
- [cosmwasm devtools](https://github.com/aswever/cosmwasm-devtools) -  A web-based console for interacting with CosmWasm smart contracts deployed locally or remotely. Can use Keplr account or generate new addresses as needed. Visit the tool [here](https://cosmwasm.tools/).
- [cosmwasm/ts-codegen](https://github.com/CosmWasm/ts-codegen) - Convert your CosmWasm smart contracts into dev-friendly TypeScript classes so you can focus on shipping code.

## dApps

Looking for dApps to feature. See
[#19](https://github.com/CosmWasm/cw-awesome/issues/19).
