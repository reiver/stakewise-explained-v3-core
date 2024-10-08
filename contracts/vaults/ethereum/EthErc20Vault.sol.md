# EthErc20Vault (contract)

As the name suggests, **EthErc20Vault** is a StakeWise vault that fits the popular [ERC-20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) (fungible token) interface.

To other _contracts_ call its constructor:

* [EthBlocklistErc20Vault](../../../contracts/vaults/ethereum/EthBlocklistErc20Vault.sol.md)
* [EthPrivErc20Vault](../../../contracts/vaults/ethereum/EthPrivErc20Vault.sol.sol.md)

EthErc20Vault is:

* [VaultImmutables](../../../contracts/vaults/modules/VaultImmutables.sol.md)
* Initializable ([openzeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/Initializable.sol))
* [VaultAdmin](../../../contracts/vaults/modules/VaultAdmin.sol.md)
* [VaultVersion](../../../contracts/vaults/modules/VaultVersion.sol.md)
* [VaultFee](../../../contracts/vaults/modules/VaultFee.sol.md)
* [VaultState](../../../contracts/vaults/modules/VaultState.sol.md)
* [VaultValidators](../../../contracts/vaults/modules/VaultValidators.sol.md)
* [VaultEnterExit](../../../contracts/vaults/modules/VaultEnterExit.sol.md)
* [VaultOsToken](../../../contracts/vaults/modules/VaultOsToken.sol.md)
* [VaultMev](../../../contracts/vaults/modules/VaultMev.sol.md)
* [VaultToken](../../../contracts/vaults/modules/VaultToken.sol.md)
* [VaultEthStaking](../../../contracts/vaults/modules/VaultEthStaking.sol.md)
* [Multicall](../../../contracts/base/Multicall.sol.md)
* [IEthErc20Vault](../../../contracts/interfaces/IEthErc20Vault.sol.md)

## Functions

* `function initialize(bytes calldata params) external payable virtual override reinitializer(_version)` — 
