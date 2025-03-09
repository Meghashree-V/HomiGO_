# HomiGO  
HomiGO is a Web3-based decentralized rental platform that enables users to book rentals and make payments in cryptocurrency while allowing property owners to list their properties securely.

---
## Workflow Overview  

### 1. Home Page - Search for Rentals  
Users can enter:  
- **Check-in & Check-out Dates**  
- **Location**  
- **Number of Guests**  
- Click the **Search** button to view available rentals.  

Rental owners can:  
- Click **Connect Wallet** to log in.  
- Access the **Dashboard** to manage listings.
  
![home page](https://github.com/user-attachments/assets/1d3aa2a9-1141-454b-9865-e946cb2f8b3f)

---

### 2. Dashboard - User & Rental Owner View  
- Users can **view their bookings**.  
- Rental owners can **add and manage properties**.  

![Screenshot 2024-12-12 002848](https://github.com/user-attachments/assets/cf81a416-0bd2-422a-ad5f-75ac775faad7)

---

### 3. Help Center  
- Provides **FAQs**, **support guides**, and **assistance** for users and rental owners.  

![Screenshot 2024-12-13 115005](https://github.com/user-attachments/assets/91aafe6b-6ab1-4ae3-92ae-a79770a27fc3)

---

### 4. About Us  
- Information about **HomiGO’s vision**, team, and purpose.
- 
![Screenshot 2024-12-13 115105](https://github.com/user-attachments/assets/16ede05a-4a37-4864-92d5-a216dab3f03b)

---

### 5. Smart Contract Deployment Using Hardhat  
- **Deployed on a test blockchain** using **Hardhat**.
- 
![WhatsApp Image 2024-12-13 at 18 57 45_07a99493](https://github.com/user-attachments/assets/8a9832d3-910f-4e1b-a8d9-bc9111466bcd)

---

### 6. Test Accounts with 100 ETH (Ganache)  
- Generated multiple test accounts with **100 ETH** each for testing transactions.  

![Screenshot 2024-12-13 184940](https://github.com/user-attachments/assets/6253db85-b65a-42e9-b8f3-9e84de33f10f)

---


### 7. Connecting Wallet  
- Users can **connect MetaMask** to interact with the platform.  

![Screenshot 2024-12-13 190536](https://github.com/user-attachments/assets/a21c11c0-38f5-4074-b3b5-97ad94df271f)

---

### 8. Adding a New Rental  
- Owners can click **"Add New Rental"** on the dashboard.

![Screenshot 2024-12-13 191514](https://github.com/user-attachments/assets/5e0a6bf2-abbe-4e2e-b139-3b2e44cd3997)

#### Fill in Rental Details  
- Property **Name, Location, Description, Price (USD), and Max Guests**.  
- Upload rental **images**.
  
![Screenshot 2024-12-13 191654](https://github.com/user-attachments/assets/9b9220e1-9caa-4dd6-aff3-b22e9013ff6b)

#### Rental Added Successfully  
- Property is now listed on the platform.  

![Screenshot 2024-12-13 191725](https://github.com/user-attachments/assets/4889f7ca-99f4-409e-acc8-5abf112474c9)

---

### 9. Booking a Rental as a User  
- Switch to a **different account** and book a listed rental.  

![Screenshot 2024-12-13 192001](https://github.com/user-attachments/assets/a5a43003-ecc5-43c8-bc6c-ade92564a376)

C#### Confirm Booking Details  
- Review property and rental duration.

![Screenshot 2024-12-13 192026](https://github.com/user-attachments/assets/2a103fec-e143-452f-a3ee-4c803dffef03)


#### Booking Confirmed  
- Transaction is completed, and the booking is stored on the blockchain.
- 
![Screenshot 2024-12-13 192047](https://github.com/user-attachments/assets/136c527f-ff3a-47f5-a9c8-518b1f6a40bd)

---

### 10. Storing Rental Images on IPFS (Using Pinata)  
- All uploaded rental images are stored on **IPFS** via **Pinata** for decentralized storage.  

![WhatsApp Image 2024-12-13 at 19 45 05_8b2e41d9](https://github.com/user-attachments/assets/03d7154c-5db4-4cb5-bf4c-52358e931ea6)

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

