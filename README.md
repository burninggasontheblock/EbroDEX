# EBRODEX

EBRODEX is a decentralized exchange (DEX) implemented on the Ethereum blockchain. This smart contract facilitates token swaps, liquidity provision, and liquidity removal using an Automated Market Maker (AMM) model. It supports Ethereum and an ERC-20 token as the trading pair.

---

## Features

- **Add Liquidity:** Users can deposit Ethereum and tokens to provide liquidity and earn LP (Liquidity Provider) tokens.
- **Remove Liquidity:** Liquidity providers can redeem their LP tokens to withdraw their share of the pool.
- **Swap Tokens:** 
  - Swap Ether for tokens.
  - Swap tokens for Ether.
- **Dynamic Pricing:** Uses a constant product formula for token pricing with a 1% fee on swaps.

---

## Smart Contract Details

### `DEX.sol`

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

import "@thirdweb-dev/contracts/base/ERC20Base.sol";

contract DEX is ERC20Base {
    address public token;

    constructor(
        address _token,
        address _defaultAdmin,
        string memory _name,
        string memory _symbol
    ) ERC20Base(_defaultAdmin, _name, _symbol) {
        token = _token;
    }

    function getTokensInContract() public view returns (uint256) {
        return ERC20Base(token).balanceOf(address(this));
    }

    function addLiquidity(uint256 _amount) public payable returns (uint256) {
        // Add liquidity logic here
    }

    function removeLiquidity(uint256 _amount)
        public
        returns (uint256, uint256)
    {
        // Remove liquidity logic here
    }

    function getAmountOfTokens(
        uint256 inputAmount,
        uint256 inputReserve,
        uint256 outputReserve
    ) public pure returns (uint256) {
        // Calculate token amounts
    }

    function swapEthToToken() public payable {
        // Swap Ether for tokens logic here
    }

    function swapTokenToEth(uint256 _tokenSold) public {
        // Swap tokens for Ether logic here
    }
}
```

---

## Functions

### Core Functionalities

#### `addLiquidity(uint256 _amount)`

- Adds ETH and tokens to the liquidity pool.
- Mints LP tokens to represent the user's share.
- **Input:**
  - `_amount`: Amount of tokens to add to the liquidity pool.
- **Returns:** Liquidity tokens minted.

#### `removeLiquidity(uint256 _amount)`

- Redeems LP tokens to withdraw ETH and tokens from the pool.
- **Input:**
  - `_amount`: Amount of LP tokens to redeem.
- **Returns:** ETH and tokens withdrawn.

#### `swapEthToToken()`

- Swaps ETH for tokens using the AMM pricing formula.
- **Input:** ETH sent in the transaction.
- **Output:** Tokens received.

#### `swapTokenToEth(uint256 _tokenSold)`

- Swaps tokens for ETH using the AMM pricing formula.
- **Input:**
  - `_tokenSold`: Amount of tokens to sell.
- **Output:** ETH received.

### Utility Functions

#### `getTokensInContract()`

- Returns the balance of tokens in the contract.
- **Output:** Token balance.

#### `getAmountOfTokens(uint256 inputAmount, uint256 inputReserve, uint256 outputReserve)`

- Calculates the amount of tokens received for a given input using the AMM pricing formula.
- **Input:**
  - `inputAmount`: Amount of tokens or ETH being exchanged.
  - `inputReserve`: Reserve of the input asset in the pool.
  - `outputReserve`: Reserve of the output asset in the pool.
- **Output:** Amount of output tokens.

---

## Deployment

### Prerequisites

- **Ethereum Wallet:** MetaMask or similar wallet.
- **Development Tools:** Remix, Hardhat, or Truffle.
- **Dependencies:**
  - OpenZeppelin Contracts.
  - Thirdweb Contracts.

### Steps

1. Deploy the `DEX` contract with:
   - ERC-20 token address.
   - Default admin address.
   - Name and symbol for the LP tokens.
2. Initialize liquidity by calling `addLiquidity` with ETH and tokens.

---

## Usage

1. **Adding Liquidity:**
   - Call `addLiquidity` with the desired token amount and ETH value.
   - Receive LP tokens in return.

2. **Removing Liquidity:**
   - Call `removeLiquidity` with the LP token amount.
   - Withdraw proportional ETH and tokens.

3. **Swapping ETH for Tokens:**
   - Send ETH to the contract via `swapEthToToken`.
   - Receive tokens in return.

4. **Swapping Tokens for ETH:**
   - Call `swapTokenToEth` with the token amount.
   - Receive ETH in return.

---

## Pricing Mechanism

EBRODEX uses the constant product formula:

\[ x \cdot y = k \]

Where:
- \( x \): Reserve of ETH.
- \( y \): Reserve of tokens.
- \( k \): Constant product.

A 1% fee is applied to every swap.

---

## License

This project is licensed under the UNLICENSED license.

---

Feel free to contribute or suggest improvements for EBRODEX! 🚀
