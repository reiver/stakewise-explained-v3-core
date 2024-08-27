# IMulticall (interface)

**IMulticall** seems to be borrowed from Uniswap:

* https://github.com/Uniswap/v3-periphery/blob/1d69caf0d6c8cfeae9acd1f34ead30018d6e6400/contracts/base/Multicall.sol
* https://github.com/Uniswap/v3-periphery/blob/1d69caf0d6c8cfeae9acd1f34ead30018d6e6400/contracts/interfaces/IMulticall.sol

## Functions
 
* `function multicall(bytes[] calldata data) external returns (bytes[] memory results)` — the intent of `multicall()` seems to be to make multiple function calls and return the results from the multiple function calls. It makes use of a technique mentioned here: https://ethereum.stackexchange.com/a/83577
