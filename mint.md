# This is for the creation of basic smart contract for minting a NFT

To mint an NFT

- Create a array which tracks the URLS to an Index
- This index values should be assigned to addresses(owners)
- Create a mapping which stores an array(uint datatype) as a value and the owner address as the key
-  mapping(address => uint[]) public tokensOwnedByOwner;
- The uint array contains indexes from an array
- string[] public tokenURLs

