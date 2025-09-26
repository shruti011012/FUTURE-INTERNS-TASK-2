# FUTURE_BC_Task02
# Task 2 – ERC-20 Token Development

## Theory  
I learned about smart contracts, token standards (ERC-20), and how blockchain networks execute code. I used that knowledge to build a simple token with Solidity, deploy it, and interact with its functions.

## What I Did  
- Wrote a minimal ERC-20 contract in `FutureToken.sol`.  
- Deployed it using Remix (VM or testnet).  
- Queried the `totalSupply()` function and confirmed correct behavior.  
- Added the contract code and documentation to GitHub.  

## Learnings & Reflection  
- Gained hands-on experience with Solidity and smart contract compilation.  
- Understood deployment flow and how token balances work.  
- Built confidence to write more complex contracts in the future.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FutureToken {
    string public name = "FutureToken";
    string public symbol = "FUT";
    uint8 public decimals = 18;
    uint256 public totalSupply;
    mapping(address => uint256) public balanceOf;

    event Transfer(address indexed from, address indexed to, uint256 value);

    constructor(uint256 initialSupply) {
        totalSupply = initialSupply * 10 ** uint256(decimals);
        balanceOf[msg.sender] = totalSupply;
        emit Transfer(address(0), msg.sender, totalSupply);
    }

    function transfer(address _to, uint256 _value) public returns (bool success) {
        require(balanceOf[msg.sender] >= _value, "Not enough balance");
        balanceOf[msg.sender] -= _value;
        balanceOf[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
        return true;
    }
}
