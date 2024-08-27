# IVaultFee (interface)

**IVaultFee** is used to store the vault's fee.

The usage of the word "percent" is a bit misleading — as this seems to be _basis-points_ — i.e., a percentage of a percentage.

So, for example:

* **1** means 0.01%
* **10** means 0.1%
* **100** means 1%
* **1000** means 10%
* **10000** means 100%

The function `feePercent` should probably have been called `feeBasisPoints` or `feeBPS` (rather than `feePercentage`).

IVaultFee is:

* [IVaultAdmin](IVaultAdmin.sol.md)

## Implementations

* [VaultFee](../../contracts/vaults/modules/VaultFee.sol.md)

## Events

* `event FeeRecipientUpdated(address indexed caller, address indexed feeRecipient)` — emitted when the fee recipient (i.e., who, assumingly, received the fee) is updated.

## Functions

* `function feeRecipient() external view returns (address)`   returns the address of (assumingly) who receives the fee.
* `function feePercent() external view returns (uint16)` — returns the fee-percent applied to the vault rewards; the docs says _" The Vault's fee percent in BPS"_; BPS (assumingly) = _basis points_ = 1/100th of 1 percent; i.e., a percentage or a percentage; so if this were to return 10000 that would mean 100% 
* `function setFeeRecipient(address _feeRecipient) external`— sets the address of (assumingly) who receives the fee; this can only be successfully called by the admin.
