# IVaultFee (interface)

**IVaultFee** is used to store the vault's fee.

IVaultFee is:

* [IVaultAdmin](IVaultAdmin.sol.md)

## Events

* `event FeeRecipientUpdated(address indexed caller, address indexed feeRecipient)` — emitted when the fee recipient (i.e., who, assumingly, received the fee) is updated.

## Functions

* `function feeRecipient() external view returns (address)`   returns the address of (assumingly) who receives the fee.
* `function feePercent() external view returns (uint16)` — returns the fee-percent applied to the vault rewards; the docs says _" The Vault's fee percent in BPS"_; BPS (assumingly) = _basis points_ = 1/100th of 1 percent.
* `function setFeeRecipient(address _feeRecipient) external`— sets the address of (assumingly) who receives the fee; this can only be successfully called by the admin.
