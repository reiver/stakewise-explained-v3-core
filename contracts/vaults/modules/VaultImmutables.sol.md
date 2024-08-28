# VaultImmutables (abstract contract)

The **VaultImmutables** _abstract contract_ is used to store data that cannot be changes once they are set (at the constructor).

In particular, they are used to store:

* a **keeper** — ??? [IKeeper](../../../contracts/interfaces/IKeeper.sol.md) ???
* a **vaults-registry** — 
* a **validators-registry** — 

## Internal Variables

* `address internal immutable _keeper`
* `address internal immutable _vaultsRegistry`
* `address internal immutable _validatorsRegistry`

## Internal Functions

* `function _checkHarvested() internal view`
* `function _checkCollateralized() internal view`
