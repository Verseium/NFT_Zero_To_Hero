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


### After connecting with the ERC721Connector contract

```

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// Imports
import './ERC721Connector.sol';

// Contract
contract index is ERC721Connector{


    // Constructor to create a NFT collection with name and symbol and connect with the connector
     constructor(string memory _name,string memory _symbol) ERC721Connector(_name,_symbol){

     }
}

```


### After adding mint functionality

```
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// Imports
import './ERC721Connector.sol';

// Contract
contract index is ERC721Connector{


    // Constructor to create a NFT collection with name and symbol and connect with the connector
     constructor(string memory _name,string memory _symbol) ERC721Connector(_name,_symbol){

     }


     // Functions
     // function to mint an NFT
     function mint(string memory _uri)
     public
     {
         _mint(_uri);// Bcoz the function _mint is internal
     }
}
```