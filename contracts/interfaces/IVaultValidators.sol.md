# IVaultValidators (interface)

IVaultValidators is:

* [IVaultAdmin](IVaultAdmin.sol.md)
* [IVaultState](IVaultState.sol.md)

# Events

* `event ValidatorRegistered(bytes publicKey)` — event emitted when a new validator is registered; note that this is passed a **public-key** (rather than an _address)
* `event KeysManagerUpdated(address indexed caller, address indexed keysManager)`
* `event ValidatorsRootUpdated(address indexed caller, bytes32 indexed validatorsRoot)`
* `event ValidatorsManagerUpdated(address indexed caller, address indexed validatorsManager)`
