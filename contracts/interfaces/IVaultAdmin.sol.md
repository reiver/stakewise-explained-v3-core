# IVaultAdmin (interface)

## Implementations:

* [VaultAdmin](../../contracts/vaults/modules/VaultAdmin.sol.md)

## Events

* `event MetadataUpdated(address indexed caller, string metadataIpfsHash)`

## Functions

* `function admin() external view returns (address)` — returns who the vault admin is, by returning their address
* `function setMetadata(string calldata metadataIpfsHash) external` — this function lets the admin (address) set the metadata; the metadata is given via an IPFS digest. A `MetadataUpdated` event should be emitted when this is successfully called.
