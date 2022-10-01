# This is for the creation of basic smart contract

```
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// Contract
contract index{


    // State Variables
    string public name;
    string public symbol;

    // Constructor to create a NFT collection with name and symbol
     constructor(string memory _name,string memory _symbol){

         name = _name;
         symbol = _symbol;

     }
}

```