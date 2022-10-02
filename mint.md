# This is for the creation of basic smart contract for minting a NFT

To mint an NFT

- Create a array which tracks the URLS to an Index
- This index values should be assigned to addresses(owners)
- Create a mapping which stores an array(uint datatype) as a value and the owner address as the key
-  mapping(address => uint[]) public tokensOwnedByOwner;
- The uint array contains indexes from an array
- string[] public tokenURLs


Baisc Smart Contract

```

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// For MINTING NFTS

// Imports

// Contract for Minting NFTs
contract ERC721{


    // State Variables 
    // Ararys
    // Array for storing tokenURLs and giving an index
    string[] private tokenURI;

    // Mappings


    // Mappings for storing address to the token IDS array
    mapping(address => uint[]) private tokensOwnedByOwner;


    // Functions
    // Function to create an NFT token URI into an index
    // Then to assign this NFT to an address
    function tokenID(string memory _uri)
    public{
        tokenURI.push(_uri);
        // Assigning this to the person who minted it
        tokensOwnedByOwner[msg.sender].push(tokenURI.length - 1);// tokenURI.length gives the total length and -1 gives the last index
    }

    // Function to get the tokenIDS
    function getTokenIds(address _owner)
    public
    view
    returns(uint[] memory){

        return tokensOwnedByOwner[_owner];

    }

    // Function to get the exact token details
    function getTokenValue(address _owner,uint _tokenID)
    public
    view
    returns(string memory){

        uint requiredTokenID = tokensOwnedByOwner[_owner][_tokenID];

        return tokenURI[requiredTokenID];

    }

}

```


### After optimising with a mapping


```

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// For MINTING NFTS

// Imports

// Contract for Minting NFTs
contract ERC721{


    // State Variables 
    // Ararys
    // Array for storing tokenURLs and giving an index
    string[] private tokenURI;

    // Mappings
    mapping(uint => address) public tokenOwner;


    // Mappings for storing address to the token IDS array
    mapping(address => uint[]) private tokensOwnedByOwner;


    // Functions
    // Function to create an NFT token URI into an index
    // Then to assign this NFT to an address
    function tokenID(string memory _uri)
    public{
        tokenURI.push(_uri);
        // Assigning this to the person who minted it

        uint latestID = tokenURI.length - 1;
        
        tokensOwnedByOwner[msg.sender].push(latestID);
        // tokenURI.length gives the total length and -1 gives the last index

        // Assigning token ids a owner
        tokenOwner[latestID] = msg.sender;

    }

    // Function to get the tokenIDS
    function getTokenIds(address _owner)
    public
    view
    returns(uint[] memory){

        return tokensOwnedByOwner[_owner];

    }


}

```


### Fuuly optimised code

```

// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

// For MINTING NFTS

// Imports

// Contract for Minting NFTs
contract ERC721{


    // State Variables 
    // Ararys
    // Array for storing tokenURLs and giving an index
    string[] private tokenURI;
    // Mappings
    mapping(uint => address) private tokenOwner;
    // Mappings for storing address to the token IDS array
    mapping(address => uint[]) private tokensOwnedByOwner;

    // Mappings for mapping the NFT token URI to a boolean value
    mapping(string => bool) private tokenURiExists;
    // Functions

    // Function to check whether the entered uri already exists
    function _checking(string memory _uri)
    private
    view
    returns(bool){

        return tokenURiExists[_uri];
        
    }
    // Function to create an NFT token URI into an index
    // Then to assign this NFT to an address
    function _mint(string memory _uri)
    external{

        // Require to check whether the address is not an zero address
        require(msg.sender != address(0),"Minting to an Zeroi Address");
        // Require to check whether the NFT token URI already exists? --> it shouldnt exist
        require(!_checking(_uri),"Token URI already exists");
        tokenURiExists[_uri] = true;
        tokenURI.push(_uri);
        // Assigning this to the person who minted it

        uint latestID = tokenURI.length - 1;
        
        tokensOwnedByOwner[msg.sender].push(latestID);
        // tokenURI.length gives the total length and -1 gives the last index

        // Assigning token ids a owner
        tokenOwner[latestID] = msg.sender;

    }

    // Function to get the tokenIDS
    function getTokenIds(address _owner)
    public
    view
    returns(uint[] memory){

        return tokensOwnedByOwner[_owner];

    }


}

```

