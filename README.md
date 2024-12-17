# ERC20 and Vault Contracts

## Overview
This repository contains the implementation of:
1. **ERC20 Contract** - A standard ERC20 token contract compliant with the ERC20 specification.
2. **Vault Contract** - A smart contract to facilitate secure deposits, withdrawals, and management of ERC20 tokens.

Both contracts are written in Solidity and designed for deployment on Ethereum-compatible blockchain networks.

---

## Table of Contents
1. [ERC20 Contract](#erc20-contract)
   - Features
   - Deployment Instructions
   - Example Usage
2. [Vault Contract](#vault-contract)
   - Features
   - Deployment Instructions
   - Example Usage
3. [Dependencies](#dependencies)
4. [Testing](#testing)
5. [License](#license)

---

## ERC20 Contract

### Features
The ERC20 contract implements:
- Standard ERC20 functionalities such as `transfer`, `approve`, and `transferFrom`.
- Token metadata (name, symbol, and decimals).
- Minting and burning capabilities (optional).
- Event emission for transfers and approvals.

### Functions
- **`name()`**: Returns the token name.
- **`symbol()`**: Returns the token symbol.
- **`decimals()`**: Returns the token decimals (default: 18).
- **`totalSupply()`**: Returns the total token supply.
- **`balanceOf(address account)`**: Returns the balance of a specific account.
- **`transfer(address to, uint256 amount)`**: Transfers tokens to a specified address.
- **`approve(address spender, uint256 amount)`**: Approves an allowance for a spender.
- **`transferFrom(address from, address to, uint256 amount)`**: Transfers tokens from one account to another.
- **`mint(address to, uint256 amount)`** _(if enabled)_: Mints new tokens to the specified account.
- **`burn(uint256 amount)`** _(if enabled)_: Burns tokens from the sender's account.

### Deployment Instructions
1. Ensure you have a Solidity development environment set up (e.g., [Hardhat](https://hardhat.org/) or [Remix IDE](https://remix.ethereum.org/)).
2. Compile the `ERC20` contract.
3. Deploy the contract with the following parameters:
   - `name` (string): The name of the token.
   - `symbol` (string): The token symbol.
4. (Optional) Customize the supply management (minting/burning) as needed.

### Example Usage
```solidity
// Deploy the ERC20 contract with token name "MyToken" and symbol "MTK".
ERC20 myToken = new ERC20("MyToken", "MTK");

// Transfer 100 tokens to address `0x123...`.
myToken.transfer(0x123..., 100);

// Approve 50 tokens for address `0x456...`.
myToken.approve(0x456..., 50);
```

---

## Vault Contract

### Features
The Vault contract facilitates the management of ERC20 tokens by enabling:
- Secure deposits and withdrawals of ERC20 tokens.
- Tracking of user balances.
- Event emissions for deposits and withdrawals.
- Integration with any standard ERC20 token.

### Functions
- **`deposit(uint256 amount)`**: Allows users to deposit ERC20 tokens into the vault.
- **`withdraw(uint256 amount)`**: Allows users to withdraw their ERC20 tokens.
- **`balanceOf(address account)`**: Returns the balance of tokens held in the vault by a user.
- **`token()`**: Returns the address of the ERC20 token managed by the vault.

### Deployment Instructions
1. Deploy an ERC20 token contract if not already available.
2. Deploy the `Vault` contract by specifying the address of the ERC20 token.

### Example Usage
```solidity
// Assuming `myToken` is an instance of ERC20.
Vault myVault = new Vault(address(myToken));

// User deposits 200 tokens into the vault.
myToken.approve(address(myVault), 200);
myVault.deposit(200);

// User checks their vault balance.
uint256 balance = myVault.balanceOf(msg.sender);

// User withdraws 50 tokens.
myVault.withdraw(50);
```

## Author
Venkat 
venkatahema404@gmail.com

## License
This project is licensed under the MIT License. See the LICENSE file for more details.
