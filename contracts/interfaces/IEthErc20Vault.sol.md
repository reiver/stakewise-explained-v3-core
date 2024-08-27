# IEthErc20Vault (interface)

IEthErc20Vault is:

* [IVaultAdmin](IVaultAdmin.sol.md)
* [IVaultVersion](IVaultVersion.sol.md)
* [IVaultFee](IVaultFee.sol.md)
* [IVaultState](IVaultState.sol.md)
* [IVaultValidators](IVaultValidators.sol.md)
* [IVaultEnterExit](IVaultEnterExit.sol.md)
* [IVaultOsToken](IVaultOsToken.sol.md)
* [IVaultMev](IVaultMev.sol.md)
* [IVaultToken](IVaultToken.sol.md)
* [IVaultEthStaking](IVaultEthStaking.sol.md)
* [IMulticall](IMulticall.sol.md)

## Implementations

* [EthErc20Vault](../../contracts/vaults/ethereum/EthErc20Vault.sol.md)

## Functions

* `function initialize(bytes calldata params) external payable` — used for both initializing and upgrading; the "security deposit" (for staking?) must be sent as part of call.
* `function depositAndMintOsToken(address receiver, uint256 osTokenShares, address referrer) external payable returns (uint256)` — desposits assets to the vault and mints OsToken and gives it to the receiver address; i.e.,e you can call this on someone else's behalf.
* `function updateStateAndDepositAndMintOsToken(address receiver, uint256 osTokenShares, address referrer, IKeeperRewards.HarvestParams calldata harvestParams) external payable returns (uint256)`
