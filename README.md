# StakeWise Explained: v3-core

This is a study guide for the _StakeWise v3-core source-code_<sup>[[1]](https://github.com/stakewise/v3-core)</sup>.

## Introduction

**StakeWise** is an open-source<sup>[[2]](https://github.com/stakewise)</sup> **staking application** EVM blockchain-networks.
It is primarily used on the Ethereum blockchain-network.
(The Ethereum blockchain-network is the original EVM blovkchain-network.)

The main source-code git repositories for it are:

* https://github.com/stakewise/v3-core
* https://github.com/stakewise/v3-operator

This guide focuses on https://github.com/stakewise/v3-core

## Why

One of the _needs_ for **StakeWise** (and things similar to it) come from how some blockchain-network (such as Ethereum) have minimum staking amount.

For example, on the Ethereum blockchain-network, a validator node need exactly _32 ETH_ to stake.

But what if you want to stake but you have less-than (or more-than) _32 ETH_ (that are _not_ multiples of 32)‽

That is where **StakeWise** (and things similar to it) come into play.
They let one or more people combine their ETH to stake.

For example, if Alice has _10 ETH_, Bob has _5 ETH_, and Charlie has _17 ETH_ — 10 ETH + 5 ETH + 17 ETH = 32 ETH — then they can combine their funds (through **StakeWise** (and things similar to it)) to stake.

## Where To Start

One place you can start with is:

* [EthErc20Vault](contracts/vaults/ethereum/EthErc20Vault.sol.md) <---------
* [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) & [IEthVaultFactory](contracts/interfaces/IEthVaultFactory.sol.md)

## See Also

* ERC-20
* EIP-712
* ERC-5267

## Questions & Answer

### How To Deploy Locally

1. Download the **StakeWise** `v3-core` source-code:

```
git clone https://github.com/stakewise/v3-core
```

2. Go into the directory for the (downloaded)  **StakeWise** `v3-core` source-code:

```
cd v3-core
```

3. Install the dependencies:

```
npm install
```

4. Compile the contracts:

```
npm run compile
```

5. Start a local hardhat blockchain-network node in a separate terminal:

```
npm run node
```

6. Deploy the contracts locally:

```
npm run full-deploy:eth-local
```

## Author

This guide was written by [Charles Iliya Krempeaux](http://reiver.link/)
