# IEthVaultFactory (interface)

## Events

* `event VaultCreated(address indexed admin, address indexed vault, address ownMevEscrow, bytes params)`

## Functions

* `function implementation() external view returns (address)`
* `function ownMevEscrow() external view returns (address)`
* `function vaultAdmin() external view returns (address)`
* `function createVault(bytes calldata params, bool isOwnMevEscrow) external payable returns (address vault)`
