# This is for the creation of basic smart contract for metadata of NFT


# Initial:

```

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// Contract for Metadata
contract ERC721Metadata{


    // State Variables 
    // Name and Symbol are private so that it cant be directly accessed by anyone
    // Reason: Create functions which can access these variables
    // Tihs gives more power to the NFT collection Creators on what do to before calling the functions
    string private name;
    string private symbol;

    // Constructor to create a NFT collection with name and symbol
     constructor(string memory _name,string memory _symbol){

         name = _name;
         symbol = _symbol;

     }


     // Functions to get the private variables name and symbol
     // Getter function for Name
     function getName()
     external
     view
     returns(string memory){
         return name;
     }

     // Getter function for Symbol
     function getSymbol()
     external
     view
     returns(string memory){
         return symbol;
     }
}

```
