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
- [cw1-subkeys](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw1-subkeys) by [ethanfrey](https://github.com/ethanfrey): This builds on cw1-whitelist to provide the first non-trivial solution. It still works like cw1-whitelist with a set of admins (typically 1) which have full control of the account. However, you can then grant a number of accounts allowances to send native tokens from this account. 
- [cw20-base](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-base) by [ethanfrey](https://github.com/ethanfrey): Basic implementation of a cw20 contract. It implements the [CW20](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw20/README.md) spec and is designed to be deloyed as is, or imported into other contracts to easily build cw20-compatible tokens with custom logic.
- [cw20-atomic-swap](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-atomic-swap): This is a contract that allows users to execute atomic swaps. It implements one side of an atomic swap. The other side can be realized by an equivalent contract in the same blockchain or, typically, on a different blockchain.
- [cw20-escrow](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-escrow) by [ethanfrey](https://github.com/ethanfrey): Escrow meta-contract that allows multiple users to create independent escrows.
- [cw20-staking](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw20-staking) by [ethanfrey](https://github.com/ethanfrey): This is a sample contract that releases a minimal form of staking derivatives. This is to be used for integration tests and as a foundation for other to build more complex logic upon.
- [cw3-fixed-multisig](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw3-fixed-multisig): This is a simple implementation of the [cw3 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md). It is a multisig with a fixed set of addresses created upon initialization. Each address may have the same weight (K of N) or some may have extra voting power.
- [cw4-group](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw4-group): This is a basic implementation of the [cw4 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw4/README.md). It fulfills all elements of the spec, including the raw query lookups, and it designed to be used as a backing storage for cw3 compliant contracts.
- [cw721-base](https://github.com/CosmWasm/cosmwasm-plus/tree/master/contracts/cw721-base): This is a basic implementation of a [cw721 NFT spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw721/README.md). It implements the [CW721 spec](https://github.com/CosmWasm/cosmwasm-plus/blob/master/packages/cw721/README.md) and is designed to be deployed as is, or imported into other contracts to easily build cw721-compatible NFTs with custom logic.

### Trivial Contracts

These contracts demonstrate best practices and learning references. Please do not use them in production:

- [mask](https://github.com/CosmWasm/cosmwasm-examples/tree/master/mask): The Mask works as a proxy contract that has an address and can hold tokens, and interact with other contracts like any normal user account. For more reading: [introducing the mask](https://medium.com/confio/introducing-the-mask-41d11e51bccf)
- [name service](https://github.com/CosmWasm/cosmwasm-examples/tree/master/nameservice): Blockchain name service in cosmwasm.
- [erc20](https://github.com/CosmWasm/cosmwasm-examples/tree/master/erc20): Implementation of Ethereum's [ERC20](https://eips.ethereum.org/EIPS/eip-20) interface.
- [escrow](https://github.com/CosmWasm/cosmwasm-examples/tree/master/escrow): This is a simple single-use escrow contract.
- [simple-option](https://github.com/CosmWasm/cosmwasm-examples/tree/master/simple-option): This is a simple financial option contract.
- [voting](https://github.com/CosmWasm/cosmwasm-examples/tree/master/voting): This is a simple voting contract. It creates a contract to manage token weighted polls, where voters deposit native coins in order to vote. Voters can withdraw their stake, but not while a poll they've participated in is still in progress.

## External projects

These projects/contracts are developed and maintained by CosmWasm community.

- [substrate-light-client](https://github.com/ChorusOne/substrate-light-client): Implementation of substrate light client in rust compilable to wasm. It is written to be integrated with CosmWasm readily, and is optimized to run in a constrained environment of a smart contract.
- [tendermint-light-client](https://github.com/ChorusOne/tendermint-light-client): Implementation of tendermint light client in rust compilable to wasm. The code is heavily inspired from tendermint-rs. It is optimized to run in a constrained environment of a smart contract.
- [CW20 Clawback](https://github.com/tomtau/hackatom): HackAtom V prototype of a "clawback" contract inspired by Bitcoin Vaults
- [NFT Marketplace](https://github.com/BlockscapeNetwork/hackatom_v/tree/master/contracts/marketplace): HackAtom V prototype of a "NFT Marketplace Smart Contract"

## Smart Contract Libraries

- [cosmwasm-std](https://crates.io/crates/cosmwasm-std) ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/std)): The standard library for building CosmWasm smart contracts. Code in this package is compiled into the smart contract.
- [cosmwasm-storage](https://crates.io/crates/cosmwasm-storage) ([repo](https://github.com/CosmWasm/cosmwasm/tree/master/packages/storage)): Helper methods to reduce boilerplate for storing data types. Easier and more secure persistence layer.

## Tooling

- [cosmwasm/rust-optimizer](https://github.com/CosmWasm/rust-optimizer) This is a Docker build with a locked set of dependencies to produce reproducible builds of cosmwasm smart contracts. It also does heavy optimization on the build size, using binary stripping and `wasm-opt`.

## dApps

You can find the Official Confio maintained dApp instances deployed here: [https://dapps.cosmwasm.com](https://dapps.cosmwasm.com)

- Name service: [https://dapps.cosmwasm.com/names](https://dapps.cosmwasm.com/names)
- Native wallet: [https://dapps.cosmwasm.com/wallet](https://dapps.cosmwasm.com/wallet)
- CW20 wallet: [https://dapps.cosmwasm.com/cw20-wallet](https://dapps.cosmwasm.com/cw20-wallet)
- CW20 staking service: [https://dapps.cosmwasm.com/stakes](https://dapps.cosmwasm.com/stakes)

The code is in the packages directory of the monorepo: [https://github.com/CosmWasm/dApps/tree/master/packages](https://github.com/CosmWasm/dApps/tree/master/packages)

- Name service: [https://github.com/CosmWasm/dApps/tree/master/packages/name-service](https://github.com/CosmWasm/dApps/tree/master/packages/name-service)
- Native wallet: [https://github.com/CosmWasm/dApps/tree/master/packages/wallet](https://github.com/CosmWasm/dApps/tree/master/packages/wallet)
- CW20 wallet: [https://github.com/CosmWasm/dApps/tree/master/packages/cw20-wallet](https://github.com/CosmWasm/dApps/tree/master/packages/cw20-wallet)
- CW20 staking service: [https://github.com/CosmWasm/dApps/tree/master/packages/staking-service](https://github.com/CosmWasm/dApps/tree/master/packages/staking-service)
