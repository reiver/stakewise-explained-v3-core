# EthVaultFactory (contract)

The `implementation` public variable is an something to pay attention to — and it is perhaps less straight-forward what it is because it is stored as an `address` rather than a specific `contract`.

Within the `createVault()` method, `implementation` is used as:

```solidity
// create vault
vault = address(new ERC1967Proxy(implementation, ''));
```

In the `tasks/eth-full-deploy.ts` and `tasks/eth-full-deploy-local.ts` deployment scripts, it looks like `implementation` is an instance of the following contracts:

* EthVault
* EthPrivVault
* EthBlocklistVault
* EthErc20Vault
* EthPrivErc20Vault
* EthBlocklistErc20Vault

## Is

EthVaultFactory is:

* [IEthVaultFactory](../../../contracts/interfaces/IEthVaultFactory.sol.md)

## Internal Variables

* `IVaultsRegistry internal immutable _vaultsRegistry` — [IVaultsRegistry](../../../contracts/interfaces/IVaultsRegistry.sol.md)

## Public Variables

* `address public immutable override implementation` 

* `address public override ownMevEscrow`

* `address public override vaultAdmin`
