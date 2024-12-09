<div id="top"></div>

<!-- ABOUT THE PROJECT -->
## Decentral AirBnb

This is a decentralized web3.0 version of the AirBnb renting website built for EVM compatible blockchains (Ethereum, Polygon,...), it was inspired by the Moralis project ["Build Web 3.0 AirBNB Clone Using web3uikit, React, Moralis and Solidity - Full-Stack Blockchain App"](https://www.youtube.com/watch?v=rj-Mb-xz1Os&t=2443s)

### Built With

* [Solidity](https://docs.soliditylang.org/)
* [Hardhat](https://hardhat.org/getting-started/)
* [React.js](https://reactjs.org/)
* [ethers.js](https://docs.ethers.io/v5/)
* [web3modal](https://github.com/Web3Modal/web3modal)
* [material ui](https://mui.com/getting-started/installation/)


<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
       <li><a href="#prerequisites">Prerequisites</a></li>
       <li><a href="#project-structure">Project structure</a></li>
       <li><a href="#initial-setup">Initial Setup</a></li>
      </ul>
    </li>
    <li>
      <a href="#how-it-works">How it Works</a>
     <ul>
       <li><a href="#contracts">Contracts</a></li>
       <li><a href="#user-interface">User interface</a></li>
      </ul>
    </li>
    <li><a href="#how-to-use">How to Use</a></li>
    <li><a href="#future-developements">Future developements</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>


<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

Please install or have installed the following:
* [nodejs](https://nodejs.org/en/download/) and [yarn](https://classic.yarnpkg.com/en/)
* [MetaMask](https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn) Chrome extension installed in your browser
* [Ganache](https://trufflesuite.com/ganache/) for local smart contracts deployement and testing

### Project structure

This a full stack web3 decentralized application built using Hardhat/React js, so the project is devided into 2 main parts:
<ul>
 <li><b>Smart contract/backend side:</b></li>
 Located in the hardhat folder, it contains the blockchain developement envirenment built using Hardhat, with all the smart contracts tests, deployement scripts and the plugins used (chainlink). 
  <li><b>front-end side:</b></li>
The code for the UI can be found in the src folder (as in all reactjs apps)
</ul>

### Initial Setup
1. Clone the repository and install all the required packages by running:
   ```sh
   git clone https://github.com/kaymen99/DecentralAirbnb.git
   cd DecentralAirbnb
   yarn
   ```
2. Start the ganache network and export the private key of the first account to the .env file in the hardhat folder, it will be used as admin for deploying the Airbnb contract:
   ```sh
   ETHERSCAN_API_KEY="your etherscan api key"
   POLYGON_RPC_URL="Your polygon RPC url from alchemy or infura"
   MUMBAI_RPC_URL="Your mumbai RPC url from alchemy or infura"
   PRIVATE_KEY="ganahce-private-key"
   ```


### User interface
The app allows users to rent any place in the world and pay in crypto, it's structured in 4 pages:

* The home page is the landing page of the app, By entering the city, the duration of the holiday and the number of guest the user is able to check all the available properties and can compare their prices, and the different facilities.

* The Rentals page is where the user is redirected after entering the holiday information, it contains a list of all the properties that match the user 
requirements, and also shows the location of these on a map provided by Google-maps


## How to Use

After going through all the installation and setup steps, you'll need to deploy the smart contract to the ganache network by running: 
   ```sh
   cd hardhat
   npx hardhat run scripts/deploy-airbnb.js --network ganache
   ```
This will create a config.js file and an artifacts folder and transfer them to the src folder to enable the interaction between the contract and the UI

If you want to test the functionnalities of the DecentralAirbnb contract you can do it by running:
   ```sh
   npx hardhat test
   ```
To start the app you have to go back to the DecentralAirbnb folder and run the command:
   ```sh
   yarn start
   ```
   

