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
* [EthPrivErc20Vault](contracts/vaults/ethereum/EthPrivErc20Vault.sol.md)
* [EthBlocklistErc20Vault](contracts/vaults/ethereum/EthBlocklistErc20Vault.sol.md)
* [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) & [IEthVaultFactory](contracts/interfaces/IEthVaultFactory.sol.md)
* [VaultsRegistry](contracts/vaults/VaultsRegistry.sol.md)

## See Also

* ERC-20
* EIP-712
* ERC-5267

## Questions & Answers (Q&A)

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
### Foundry Cast

Although **StakeWise** `v3-core` does _not_ use **Foundry**, you can still use **Foundry** `cast` — even when you are running **StakeWise** `v3-core` locally using hardhat.

**Foundry** `cast` can talk to a hardhat RPC-node.

### Creating A Vault

When **StakeWise** `v3-core` is deployed, it will output the address for a number of contracts.

There will be multiple [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) contracts created, and each of their addresses will be returned.

The output from the deployment script is a bit difficult to read but, you need to look for these quadruplets:

```
EthVault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthVaultFactory to VaultsRegistry
Added EthVault implementation to VaultsRegistry
```

```
EthPrivVault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthPrivVaultFactory to VaultsRegistry
Added EthPrivVault implementation to VaultsRegistry
```

```
EthBlocklistVault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthBlocklistVaultFactory to VaultsRegistry
Added EthBlocklistVault implementation to VaultsRegistry
```

```
EthErc20Vault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthErc20VaultFactory to VaultsRegistry
Added EthErc20Vault implementation to VaultsRegistry
```

```
EthPrivErc20Vault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthPrivErc20VaultFactory to VaultsRegistry
Added EthPrivErc20Vault implementation to VaultsRegistry
```

```
EthBlocklistErc20Vault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthBlocklistErc20VaultFactory to VaultsRegistry
Added EthBlocklistErc20Vault implementation to VaultsRegistry
```

Notice that the 2nd line of each quadruplet looks like:

```
EthVaultFactory deployed at 0x????????????????????????????????????????
```

The address there (that in your output will have the question-marks replace with hexadecimal digits) is the address of the [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) contract.

**BUT REMEMBER THAT THERE ARE MULTIPLE [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) CONTRACTS!**

You need to look for the version of the [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) contract for the **vault** that you want to use.

For example, if you wanted to create a [EthErc20Vault](contracts/vaults/ethereum/EthErc20Vault.sol.md) vault, then you would look for this output:

```
EthErc20Vault deployed at 0x????????????????????????????????????????
EthVaultFactory deployed at 0x????????????????????????????????????????
Added EthErc20VaultFactory to VaultsRegistry
Added EthErc20Vault implementation to VaultsRegistry
```
And then look for its [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) contract address.

...

So — given that you have the address of the [EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md) contract for the **vault** type you are interested to do, then —

The next thing you need to do is call its `createVault()` method:

* `function createVault(bytes calldata params, bool isOwnMevEscrow) external payable override returns (address vault) `

`createVault()`'s `params` parameter is opaque.
What is it‽
What should you set it to if you want to call `createVault()`‽

But we can figure out what it is —

[EthVaultFactory](contracts/vaults/ethereum/EthVaultFactory.sol.md)'s implementation of `createVault()` is:

```solidity
  function createVault(
    bytes calldata params,
    bool isOwnMevEscrow
  ) external payable override returns (address vault) {
    // create vault
    vault = address(new ERC1967Proxy(implementation, ''));

    // create MEV escrow contract if needed
    address _mevEscrow;
    if (isOwnMevEscrow) {
      _mevEscrow = address(new OwnMevEscrow(vault));
      // set MEV escrow contract so that it can be initialized in the Vault
      ownMevEscrow = _mevEscrow;
    }

    // set admin so that it can be initialized in the Vault
    vaultAdmin = msg.sender;

    // initialize Vault
    IEthVault(vault).initialize{value: msg.value}(params);

    // cleanup MEV escrow contract
    if (isOwnMevEscrow) delete ownMevEscrow;

    // cleanup admin
    delete vaultAdmin;

    // add vault to the registry
    _vaultsRegistry.addVault(vault);

    // emit event
    emit VaultCreated(msg.sender, vault, _mevEscrow, params);
  }
```

In particular, pay attention to:

```solidity
    // initialize Vault
    IEthVault(vault).initialize{value: msg.value}(params);
```

[IEthVault](contracts/interfaces/IEthVault.sol.md)'s `initialize()` function is a method that the **vaults** have to implement.

So, for example, if we look at [EthErc20Vault](contracts/vaults/ethereum/EthErc20Vault.sol.md)'s `initialize()` function:

```solidity
  function initialize(
    bytes calldata params
  ) external payable virtual override reinitializer(_version) {
    // if admin is already set, it's an upgrade
    if (admin != address(0)) {
      __EthErc20Vault_initV2();
      return;
    }
    // initialize deployed vault
    __EthErc20Vault_init(
      IEthVaultFactory(msg.sender).vaultAdmin(),
      IEthVaultFactory(msg.sender).ownMevEscrow(),
      abi.decode(params, (EthErc20VaultInitParams))
    );
  }
```
We see the `params` parameter used here:

```solidity
abi.decode(params, (EthErc20VaultInitParams))
```

And this is passed to the 3rd parameter of the `__EthErc20Vault_init()` function.

The `struct` `EthErc20VaultInitParams` is defined in the same file as [IEthErc20Vault](contracts/interfaces/IEthErc20Vault.sol.md):

```golang
  /**
   * @dev Struct for initializing the EthErc20Vault contract
   * @param capacity The Vault stops accepting deposits after exceeding the capacity
   * @param feePercent The fee percent that is charged by the Vault
   * @param name The name of the ERC20 token
   * @param symbol The symbol of the ERC20 token
   * @param metadataIpfsHash The IPFS hash of the Vault's metadata file
   */
  struct EthErc20VaultInitParams {
    uint256 capacity;
    uint16 feePercent;
    string name;
    string symbol;
    string metadataIpfsHash;
  }
```

## Author

This guide was written by [Charles Iliya Krempeaux](http://reiver.link/)
