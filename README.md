# MyToken

This Solidity program is a simple Contract program that simulates an auction and demonstrates functions and error handling of the Solidity programming language. The purpose of this program is to serve as a starting point for people like me who are new to Solidity and wants to try functions and error handling using require, assert, and revert.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has two functions that mints and burns tokens. This program serves as a simple introduction to functions and error handling in Solidity programming. It can be used as a basis and can further improve to a more complex projects in the future.

## Getting Started

### Executing program

* To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

* Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Auction {
    address private owner;
    uint public highestBid;
    address public highestBidder;
    bool public auctionEnded;

    constructor() {
        owner = msg.sender;
        highestBid = 0;
        auctionEnded = false;
    }

    function bid(uint _amount) public {
        require(!auctionEnded, "Sorry, Auction has already ended!");
        require(msg.sender != owner, "Sorry, Owner cannot bid!");
        require(_amount > highestBid, "Bid must be higher than the current highest bid.");

        highestBid = _amount;
        highestBidder = msg.sender;

        assert(highestBid == _amount);
        assert(highestBidder == msg.sender);
        if (!(highestBid == _amount && highestBidder == msg.sender)) {
            revert("Bid update failed!");
        }
    }

    function endAuction() public {
        require(msg.sender == owner, "Only the owner can end the auction.");
        require(!auctionEnded, "Auction has already ended!");

        auctionEnded = true;

        assert(auctionEnded);
        if (!auctionEnded) {
            revert("Auction end failed!");
        }
    }

    function getHighestBid() public view returns (uint) {
        return highestBid;
    }

    function getHighestBidder() public view returns (address) {
        return highestBidder;
    }

    function hasAuctionEnded() public view returns (bool) {
        return auctionEnded;
    }
}
```

* To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

* Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Auction" contract from the dropdown menu. Select a test address from Account tab, and then click on the "Deploy" button.

* After deploying the first account, deploy 2 more accounts by selecting another test address from the Account tab and click on the "Deploy" button.

* Once the 3 accounts are deployed, you can interact with it by checking the getHighestBid, getHighestBidder, and hasAuctionEnded functions to check their values. After checking their values, you can start by bidding using the first address. Enter a non-negative value into the field beside the bid button, after click on the "bid" button.

* You can now then call the getHighestBid and getHighestBidder function that will return a value and an address. Then, try entering a value that is lower than the highestBid to check if the program will display an error message. Then, Click on the endAuction, it will display an error message.

* Once the error message has displayed, try entering a value in the bid section that is greater than the highestBid. After, you can now then check if the auction has already ended by clicking on the hasAuctionEnded button. 

* Lastly, select the third address and try entering a value in the bid field. It will prompt an error message since it is the owner. Click on the endAuction button to end the auction. By clicking on the hasAuctionEnded, it will return a value of true. 

## Authors

[Miguel Andre Encomienda](https://www.linkedin.com/in/miguel-encomienda-526593292/)


## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details