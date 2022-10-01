# This is for the creation of ERC721Connector

```
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// Imports

import './ERC721Metadata.sol';

// Contract for Connector contract with inheriting ERC721Metadata.sol
contract ERC721Connector is ERC721Metadata{


    // State Variables 
    // No need as the name and symbol will pass into ERC721Metadata.sol

    // Constructor to create a NFT collection with name and symbol
     constructor(string memory _name,string memory _symbol) ERC721Metadata(_name,_symbol){

     }

}

```