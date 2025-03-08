# HomiGO  

HomiGO is a **decentralized Web3.0** rental platform built for **EVM-compatible blockchains** (Ethereum, Polygon, etc.). It enables users to list and rent properties worldwide while making payments in cryptocurrency.  

---

## Built With  

- **Solidity**  
- **Hardhat**  
- **React.js**  
- **ethers.js**  
- **web3modal**  
- **Material UI**  

---

## Table of Contents  

- [Getting Started](#getting-started)  
- [Project Structure](#project-structure)  
- [How It Works](#how-it-works)  
- [How to Use](#how-to-use)  

---

## Getting Started  

### Prerequisites  
Make sure you have the following installed before proceeding:  

- **Node.js & Yarn**  
- **MetaMask Browser extension(for whichever browser you are using)**  
- **Ganache** (for local smart contract deployment and testing)  

### Initial Setup  

1. Clone the repository and install dependencies:  

   ```sh
   git clone https://github.com/your-github/HomiGO.git
   cd HomiGO
   yarn
   ```

2. Start **Ganache** and export the private key of the first account to the `.env` file in the **hardhat** folder:  

   ```plaintext
   ETHERSCAN_API_KEY="your-etherscan-api-key"
   POLYGON_RPC_URL="your-polygon-rpc-url"
   MUMBAI_RPC_URL="your-mumbai-rpc-url"
   PRIVATE_KEY="your-ganache-private-key"
   ```

3. **Set up IPFS storage**  
   HomiGO supports **IPFS storage** for rental images. You can use **Pinata** or **web3.storage** for this purpose.  

   #### Using Pinata  
   1. Create a free account on **[Pinata](https://www.pinata.cloud/)**.  
   2. Generate an **API key** from the **API Keys** section.  
   3. Add the API key to `src/utils/StoreContent.js`:  

      ```js
      const pinata_api_key = "YOUR-PINATA-API-KEY";
      ```

4. **Set up Google Maps API**  
   Obtain a free API key from Google and add it to `src/component/RentalsMap.js`:  

   ```js
   export default GoogleApiWrapper({
       apiKey: "YOUR-GOOGLE-MAPS-API-KEY",
   })(RentalsMap);
   ```

   **For Development Mode**  
   If you leave `apiKey: ""`, Google Maps will still work **for development purposes**, but the locations may not be accurate. It is recommended to use a valid API key for full functionality.  

---

## Project Structure  

HomiGO is a **full-stack Web3 decentralized application** built using **Hardhat** and **React.js**, divided into two main parts:  

### 1. Smart Contract / Backend (Hardhat Folder)  
- Contains all **smart contracts**, **tests**, and **deployment scripts**.  
- Uses **Chainlink price feeds** for rental pricing in stable USD.  

### 2. Frontend (src Folder)  
- Built using **React.js** and **Material UI**.  
- Connects to the blockchain via **ethers.js**.  

---

## How It Works  

### Smart Contract (DecentralAirbnb.sol)  

#### Core Functions  
- `addRental` → Allows users to list properties for rent (requires a small fee).  
- `bookDates` → Books a rental for selected dates if available.  
- `checkIfBooked` → Verifies if a rental is booked for the given dates.  

#### Admin Functions  
- `changeListingFee` → Adjusts the listing fee for new rentals.  
- `withdrawBalance` → Allows the admin to withdraw the accumulated contract balance.  

#### ChainLink Price Feed  
- Rentals are priced in **USD** but paid in **ETH/MATIC**.  
- **Chainlink oracles** convert the price dynamically during booking.  

---

## User Interface  

HomiGO allows users to **rent properties worldwide** and **pay in crypto**. The platform consists of four main pages:  

1. **Home Page**  
   - Users enter the **city**, **dates**, and **number of guests**.  
   - Displays all available properties that match the search criteria.  

2. **Rentals Page**  
   - Shows a list of properties matching the user's search.  
   - Displays property locations on an **interactive Google Map**.  

3. **User Dashboard**  
   - Accessed by clicking the **Account** button.  
   - Displays **listed properties** and **booked reservations**.  

4. **Add Rental Page**  
   - Users can list new properties by providing:  
     - **Property name, city, coordinates (latitude/longitude), description, max guests, and rental price in USD**.  
   - Exact **latitude and longitude** are crucial for displaying the property on **Google Maps**.  

---

## How to Use  

After setting up the project, follow these steps to deploy and run HomiGO:  

1. **Deploy the smart contract to Ganache**  

   ```sh
   cd hardhat
   npx hardhat run scripts/deploy-airbnb.js --network ganache
   ```

   - This generates a **config.js** file and an **artifacts** folder.  
   - These files are automatically moved to the `src` folder for frontend interaction.  

2. **Run contract tests**  

   ```sh
   npx hardhat test
   ```

3. **Start the frontend application**  

   ```sh
   cd ..  
   yarn start
   ```

---

