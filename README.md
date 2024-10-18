# Solidity Learning Journey 🚀

## Update Kedua: Membuat Token ERC-20 Sederhana di Ethereum

Setelah mempelajari dasar-dasar Solidity dan membuat smart contract sederhana, sekarang saya akan membahas sesuatu yang lebih kompleks: **membuat token ERC-20**. ERC-20 adalah standar yang digunakan untuk membuat token di jaringan Ethereum, dan banyak token di dunia kripto yang menggunakan standar ini.

### 1. Apa Itu Token ERC-20?
ERC-20 adalah standar untuk token yang memungkinkan token untuk berinteraksi satu sama lain di Ethereum dengan cara yang seragam. Ini mencakup fungsi dasar seperti transfer token, mengecek saldo token, dan lain-lain.

### 2. Membuat Token ERC-20 Sederhana

Di sini, saya membuat token sederhana yang disebut **MyToken**. Berikut adalah kode smart contract-nya:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor() ERC20("MyToken", "MTK") {
        _mint(msg.sender, 1000 * 10 ** decimals());  // Mint 1000 tokens to deployer
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}
