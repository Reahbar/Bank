# Smart Contract Management 
# Project: Function Frontend

In this project, we are going to demonstrate the basic smart contract integration with the front end."

## Description

In this project, you can see multiple files, but let's start from the "contract" folder. Inside the "contract" folder, there is a contract named "Assessment.sol" which is designed for a Web3.0 ATM. It is written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. This contract is created according to the requirements defined on the Metacrafters website in the "Assessment Smart Contract Management - ETH + AVAX Project: Function Frontend" section.

Within this smart contract, there are three functions are defined. The first function is used for depositing ether (deposit), the second one is for checking the balance (getBalance), and the third function is for withdrawing ether (withdraw).

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website or Remix - Etheruem IDE. Create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., FunctionsAndErrosChallenge.sol). Copy and paste the following code into the file:

### Code
```javascript
// SPDX-License-Identifier: MIT

pragma solidity 0.8.0;

/*
        Project must provide the following to be successfully completed:
   
Functionality

    Contract successfully uses require()
    Contract successfully uses assert()
    Contract successfully uses revert() statements

Explanation

    Code read-aloud is submitted
    Code read-aloud is complete (all steps explained)
    Code read-aloud is clear and understandable

*/

// SPDX-License-Identifier: MIT

/*Functionality

    Contract successfully uses require()
    Contract successfully uses assert()
    Contract successfully uses revert()

Explanation

    Code read-aloud is submitted
    Code read-aloud is complete (all steps explained)
    Code read-aloud is clear and understandable */

pragma solidity ^0.8.0;

contract BasicBankContract 
    {
    mapping (address => uint) balance;
    address owner;

    constructor () {
        owner = msg.sender;
    }

    modifier onlyOwner 
    {
        require (owner == msg.sender, "Warning you are not the owner");_;
    }
    
    function getDeployerAccountAddress () onlyOwner public view returns (address) 
    {
        address account = msg.sender;
        assert (owner == account);
        return account;
    }

     function deposit () public payable
    {   require (msg.value > 0, "Amount must be greater than 0");
        balance [msg.sender] += msg.value;
    }
    
    function getBalance () onlyOwner public view returns (uint)
    {  
        return balance [msg.sender]; 
    }

    function withdraw(uint amount) payable public 
    {
    require(amount > 0, "Amount must be greater than zero");
    require(balance[msg.sender] >= amount, "Insufficient balance");
    payable(msg.sender).transfer(amount);
    }

    function transferBalance(address _receiver, uint _amount) public payable 
    {
        if (balance[msg.sender] < _amount) 
    {
        revert("Insufficient balance");
    }
        balance[msg.sender] -= _amount;
        balance[_receiver] += _amount;
    }


}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile Token.sol" button.
## Explanation
https://www.loom.com/share/44de64d9442b4a4fb5608b89ae92d83f
## Authors

Contributors names and contact info

ex. Reahbar Khan  
ex. https://github.com/Reahbar


## License

This project is licensed under the [MIT] License - see the LICENSE.md file for details
