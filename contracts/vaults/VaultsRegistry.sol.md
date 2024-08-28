# VaultsRegistry (contract)

When you deploy the **StakeWise** `v3-core` contracts, you get messages like these:

```
VaultsRegistry deployed at 0x????????????????????????????????????????
Added EthVaultFactory to VaultsRegistry
Added EthVault implementation to VaultsRegistry
Added EthPrivVaultFactory to VaultsRegistry
Added EthPrivVault implementation to VaultsRegistry
Added EthBlocklistVaultFactory to VaultsRegistry
Added EthBlocklistVault implementation to VaultsRegistry
Added EthBlocklistVault implementation to VaultsRegistry
Added EthErc20Vault implementation to VaultsRegistry
Added EthPrivErc20VaultFactory to VaultsRegistry
Added EthPrivErc20Vault implementation to VaultsRegistry
Added EthBlocklistErc20VaultFactory to VaultsRegistry
Added EthBlocklistErc20Vault implementation to VaultsRegistry
Added EthGenesisVault to VaultsRegistry
Added EthGenesisVault implementation to VaultsRegistry
Added EthFoxVault to VaultsRegistry
Added EthRestakeVaultFactory to VaultsRegistry
Added EthRestakePrivVaultFactory to VaultsRegistry
Added EthRestakeBlocklistVaultFactory to VaultsRegistry
Added EthRestakeErc20VaultFactory to VaultsRegistry
Added EthRestakePrivErc20VaultFactory to VaultsRegistry
Added EthRestakeBlocklistErc20VaultFactory to VaultsRegistry
VaultsRegistry ownership transferred to 0x????????????????????????????????????????                                                                                                
```

One thing that this suggests is that `VaultsRegistry` is holding references to the various **factories** for creating **vaults**.

Within the `VaultsRegistry` source-code, we see the public variables:

```solidity
mapping(address => bool) public override factories;
```

[IVaultsRegistry](../../contracts/interfaces/IVaultsRegistry.sol.md) definition for this is:

```solidity
/**
 * @notice Registered Factories
 * @param factory The address of the factory to check whether it is whitelisted
 * @return `true` for the whitelisted Factory, `false` otherwise
 */
function factories(address factory) external view returns (bool);
```



## Is

VaultsRegistry is:

* Ownable2Step ([openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable2Step.sol))
* [IVaultsRegistry](../../contracts/interfaces/IVaultsRegistry.sol.md)
