# IVaultsRegistry (interface)

## Implementations

* [VaultsRegistry](../../contracts/vaults/VaultsRegistry.sol.md)

## Events

* `event VaultAdded(address indexed caller, address indexed vault)`
* `event VaultImplAdded(address indexed impl)`
* `event VaultImplRemoved(address indexed impl)`
* `event FactoryAdded(address indexed factory)`
* `event FactoryRemoved(address indexed factory)`

## Functions

* `function vaults(address vault) external view returns (bool)`
* `function vaultImpls(address impl) external view returns (bool)`
* `function factories(address factory) external view returns (bool)`
* `function addVault(address vault) external`
* `function addVaultImpl(address newImpl) external`
* `function removeVaultImpl(address impl) external`
* `function addFactory(address factory) external`
* `function removeFactory(address factory) external`
* `function initialize(address _owner) external`
