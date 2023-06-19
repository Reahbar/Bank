# Smart Contract Management 
# Project: Function Frontend

In this project, we demonstrate the integration of a basic smart contract named "Assessment." To compile and deploy the smart contract, we utilize the Hardhat development environment. For the integration with the frontend, we employ the web3.js library!

## Description

In this project, you can see multiple files, but let's start from the "contract" folder. Inside the "contract" folder, there is a contract named "Assessment.sol" which is designed for a Web3.0 ATM. It is written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. This contract is created according to the requirements defined on the Metacrafters website in the "Assessment Smart Contract Management - ETH + AVAX Project: Function Frontend" section.

Within this smart contract, there are three functions are defined. The first function is used for depositing ether (deposit), the second one is for checking the balance (getBalance), and the third function is for withdrawing ether (withdraw).

In the project "pages" folder. Inside the "index.js" you can see a "React" component, called "HomePage," enables users to interact with a Web3.0 ATM smart contract on Ethereum. It utilizes MetaMask for wallet integration and ethers.js library for contract interaction. Users can connect their wallets, view their account balance, and perform deposit and withdrawal transactions. It provides a seamless and secure Web 3.0 banking experience.

In the project "scripts" folder inside the "deploy.js" you can see the script utilizes the Hardhat development environment to deploy a smart contract called "Assessment" with an initial balance of 0 ETH. It retrieves the contract factory, deploys the contract, and logs the deployment details, including the contract's address. The script follows the async/await pattern and handles errors appropriately.

Inside the project below the "script" folder, you can find five files. Four of these files are related to Hardhat, which is the development environment used for this project. The Second file below the ".gitignore" is named "License" and is part of the MIT License, which governs the usage of this project.


## Getting Started

### Executing program

To run this project using Visual Studio Code, follow these steps:

1 - Copy the project permalink and open Visual Studio Code.
2 - Use the "git clone" command followed by the permalink to clone the project into your local directory.
3 - Inside the project directory, open the terminal and run the command "npm i" to install the project dependencies.
4 - Open two additional terminals in Visual Studio Code.
5 - In the second terminal, run the command "npx hardhat node". If you encounter an error, fix it by running the command "npm install --save-dev @nomicfoundation/hardhat-toolbox" and then try "npx hardhat        node" again. This command starts a local development blockchain with a set of accounts.
6 - Copy the private key of one of the accounts displayed in the second terminal.
7 - In the third terminal, run the command "npx hardhat run --network localhost scripts/deploy.js". This command compiles and deploys the smart contract using the Hardhat development environment.
8 - Open an integrated terminal in the "scripts" folder and run the command "npm run dev". This command launches the frontend of the project.
9 - After completing these steps, the project should be running on your local machine at http://localhost:3000/.

# Make sure MetaMask is installed on your computer! 

Open MetaMask and select the "Ethereum Mainnet" network. Then, click on "Add a network" and choose "Add a network manually." In the "Network name" field, you can enter a name for the network (e.g., "Custom Network"). In the "New RPC URL" box, enter "http://127.0.0.1:8545/". Set the "Chain ID" to "31337". You can enter a currency symbol of your choice. You can skip the "Block explorer URL" field.

### Code
```javascript
// SPDX-License-Identifier: MIT

// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

//import "hardhat/console.sol";

contract Assessment 
{
    uint256 public balance;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);

    constructor(uint initBalance) payable 
    {
        balance = initBalance;
    }

    function getBalance() public view returns(uint256)
    {
        return balance;
    }

    function deposit(uint256 _amount) public payable 
    {
        uint _previousBalance = balance;

        // make sure this is the owner

        // perform transaction
        balance += _amount;

        // assert transaction completed successfully
        assert(balance == _previousBalance + _amount);

        // emit the event
        emit Deposit(_amount);
    }

    // custom error
    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public 
    {
        uint _previousBalance = balance;
        if (balance < _withdrawAmount) 
        {
            revert InsufficientBalance
        ({
                balance: balance,
                withdrawAmount: _withdrawAmount
            });
        }

        // withdraw the given amount
        balance -= _withdrawAmount;

        // assert the balance is correct
        assert(balance == (_previousBalance - _withdrawAmount));

        // emit the event
        emit Withdraw(_withdrawAmount);
    }
}

```
## Authors

Contributors names and contact info

ex. Reahbar Khan  
ex. https://github.com/Reahbar


## License

This project is licensed under the [MIT] License - see the LICENSE.md file for details
