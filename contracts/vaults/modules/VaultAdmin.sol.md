# VaultAdmin (abstract contract)

VaultAdmin is:

* Initializable ([openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/Initializable.sol))
* [IVaultAdmin](../../../contracts/interfaces/IVaultAdmin.sol.md)

# Events

* ` event MetadataUpdated(address indexed caller, string metadataIpfsHash)`

# IVaultAdmin Functions

* `address public override admin` — stores and returns the admin address.
* `function setMetadata(string calldata metadataIpfsHash) external override` — sets the metadata; the metadata is stored off (this) chain, on IPFS; it seems like this data is stored in the `MetadataUpdated` event.

# Functions

* `function __VaultAdmin_init(address _admin, string memory metadataIpfsHash) internal onlyInitializing` — an initialization function that sets the owner, and sets the metadata.
