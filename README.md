Project Title
Simple overview of use/purpose.

Description
This project is a simple smart contract written in Solidity that demonstrates the usage of require(), assert(), and revert() statements. The contract represents a basic balance management system, allowing users to deposit and withdraw funds while enforcing certain conditions.

Getting Started
Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.s

Executing program
we have two functions: deposit() and withdraw(). Both functions use the require() statement to check for specific conditions before proceeding with the operation. 
The require() statement will revert the transaction if the condition is not met.
The deposit() function also uses the assert() statement to check that the balance does not exceed 100. 
The assert() statement will revert the transaction if the condition is not met, but it will not return any unused gas. This is different from require(), which will refund any unused gas.
The withdraw() function uses the revert() statement to revert the transaction if the withdrawal would put the balance below zero.
The revert() statement will undo all changes made to the state during the transaction, including the withdrawal itself.

//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    uint public balance;

    function deposit(uint _amount) public {
        require(_amount > 0, "Amount must be greater than zero.");
        require(address(this).balance + _amount <= 100, "Balance cannot exceed 100.");

        balance += _amount;
        assert(balance <= 100);
    }

    function withdraw(uint _amount) public {
        require(_amount > 0, "Amount must be greater than zero.");
        require(balance >= _amount, "Insufficient balance.");

        balance -= _amount;
        if (balance < 0) {
            revert("Withdrawal would put balance below zero.");
        }
    }
}


Authors
Contributors names and contact info

Carlsly June D butt
BSIT 3.4

License
This project is licensed under the [Carlsly June D butt] License - see the LICENSE.md file for details
