# Decentralized Online Marketplace
## Consensys Academy Final Project

#### Additional Internal Documentation
- [Design Pattern Documentation](documentation/design_pattern_decisions.md)
- [Avoiding Common Attacks Documentation](documentation/avoiding_common_attacks.md)

#### Application Overview
An online decentralized marketplace. 

The filed repository contains an Ethereum Marketplace decentralized or DApp. The following details specify the design task as outlined by ConsenSys Academy 2018. Description: Create an online marketplace that operates on the blockchain. There are a list of stores on a central marketplace where shoppers can purchase goods posted by the store owners. The central marketplace is managed by a group of administrators. Admins allow store owners to add stores to the marketplace. Store owners can manage their store’s inventory and funds. Shoppers can visit stores and purchase goods that are in stock using cryptocurrency. The included smart contracts were developed in Solidity using the Truffle framework. The user interface was developed using React and reactstrap.

// Application Details
The application supports the following user accounts:
- Admins - Responsible for approving shop owner requests
- Store Owners - Create stores, add products, sell stuff, make Ether
- Shoppers - Browse stores, purchase products

// Steps to Install & Run
// The following applications should be installed on your computer prior to initializing the attached files:
Node.js, ganache-cli, Truffle and Metamask within your Chrome browser.

Download/Clone the code repository.

Within your personal terminal, locate the folder as labelled MarketplaceDapp.
To open these files, change directory to MarketplaceDapp and install required npm package files.

```
cd MarketplaceDapp
npm install
```
Atom, Sublime Text and other text editing applications may be used to open and view source code.

Upon first deploying the marketplace contract, the account that deploys the contract is the first Admin. The marketplace starts with no store owners, no stores, no products. 

Users can shop at available stores and purchase products by spending Ether. Users can also request to become store owners (with admin approval).

Once granted store ownership approval, new store owners can create stores, add products, and sell on the marketplace. 

When users purchase products from a given store, inventory is adjusted, Ether is held in the store for store owners to withdraw.

#### Setup/Run Steps
**Note 1:** These steps assume you have NodeJS, NPM, Truffle, Git and MetaMask already set up. If you are missing any of those dependencies, please find their respective documentation online and set them up first.

**Note 2:** These instructions use truffle develop instead of the ganache-cli to run a local blockchain. If you are used to ganache, please note the default port for truffle develop is different, so please follow the below steps carefully. 

1. Open a terminal session and navigate to the location you'd like to store a copy of the repo in. 
1. Clone the rep
1. Move into the root directory of the project: `cd marketplace_dapp`.
1. Install ETHpm library dependencies (Open Zeppelin): `truffle install`.
1. Start a local blockchain using truffle: `truffle develop`.
1. Inside the truffle console (which you should now be in), migrate smart contracts: `migrate`.
1. Open a second terminal window and navigate to the root directory of the project.
1. Install front end dependencies via npm: `npm install`.
1. Build the front end react app and open it in the browser (at http://localhost:3000): `npm run start`.
1. Open MetaMask and connect to the truffle blockchain via standard process (seed phrase, custom RPC - if necessary, see MetaMask + Truffle documentation).
1. Refresh

If you followed all these steps correctly, you should land on the Admin Page, and your account address should display on the right side of the header.

If you ever encounter an issue, please see the Issues section below.

/ Application Functionality
This DApp initiates by confirming if administrative access has been acquired by the user. If web3 is located within the browser through the Metamask application, the user will be designated access to the application.
Assigned administrators can access file contents through Metamask Account 2 from the displayed system dropdown menu.

Users will be directed to a page of active contents available for purchase.
To add a new listing, select ```Request Store Ownership```

A list of all active listings is displayed under the "All Listings" tab.  If there are no active listings, the application displays "No active listings...". Metamask will display an authorization prompt to confirm if you wish to proceed with the intended transaction. 15 seconds after you confirm the transaction, when the block for the transaction has been mined, the new listing will appear under both ```All Listings``` and ```My Listings``` tabs.

Switching between Metamask accounts enables the user to view how information is viewed from an administrative perspective and shopper perspective. Account 1 provides administrator access while account 2 provides an informational overview of administrative transactions made. If you create and/or switch to "Account 2" in MetaMask and then reload the page, the page will update to reflect the new Account 2 address and balance.
Switching back to "Account 1" brings you back to the administrative section and enables the user to view purchase requests from "Account 2" users.

Clicking the "Approve" and "Submit" buttons ill display pending transaction for the price of the listing.  After transaction completion the listing will disappear from ```All Listings``` tab and your displayed balance will decrease by the price of the listing.  

Open MetaMask and navigate back to Account 2, and reload. You should now land on the Store Owner page.

The UI should react to the updates, and eventually render your new store in the bottom section of the page.
Add a product or two by filling in the form at the bottom of the store widget, clicking submit, and verifying via MetaMask.

Now that you've got some products to sell on the marketplace, it's time to assume the role of the shopper.

Open MetaMask and select Account 3 and reload.

As this account hasn't done anything on the marketplace yet, the default Shopper page should load.

When the transaction is confirmed and completed, the system will be frozen.  If you now attempt to create, cancel or buy a listing, an alert will display and the transaction will be blocked.

As Account 3, you can now input a quantity to purchase of a given product, and click the purchase button to make a purchase in ETH. Verify in Metamask after it pops up. You've new successfuly paid for a product using ETH, and sent that ETH to the store contract, which allows only the store owner to withdraw.

#### Running Tests
1. From the project root start the truffle development blockchain: `truffle develop`.
1. Execute all unit tests: `test`.

#### Issues
MetaMask transaction nonce doesnt' match local blockchain:
1. Reset all accounts in MetaMask (via settings in the MetaMask UI)
1. Re-migrate and reset accounts and contracts from truffle development environment: `migrate --reset`.

`truffle migrate` fails:
1. Usually this occurs when contracts have been migrated before, and the JSON ABI files are pointing to the old addresses. Fix by re-running migrations with the reset flag: `migrate --reset`.

MetaMask won't connect to the local blockchain.
1. It's possible you are running against the wrong port. The instructions use the new truffle develop blockchain, which runs on port `9545` compared to the ganache-cli blockchain that runs on port `8545`. Make sure you set your local RPC in the MetaMask UI to point to `9545`.
