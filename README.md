


# DIDLab Assignment 4 — Minimal ERC-20 DApp UI

## Narrative
This project is the implementation of **Assignment 4: Minimal DApp** for DIDLab.  
The goal was to build a simple web-based decentralized application (DApp) that connects to **MetaMask**, switches to the correct **DIDLab network**, loads our deployed **ERC-20 token**, shows balances, and enables **token transfers**.  

The DApp was designed with usability in mind:  
- Clear **connect flow** with MetaMask integration.  
- Automatic **network switching** to the Team 10 DIDLab chain.  
- **Persistent token config** via localStorage.  
- **Balance refresh** triggered by events or manually.  
- Transfer flow with detailed transaction logs.  
- Optional ability to add the token to MetaMask for visibility.  

  ### Short Note

- During the development of this DApp, I added several safety and usability touches to improve the user experience:

- Error Handling: The DApp logs clear error messages when a token address is invalid, when MetaMask is not available, or if the user forgets to enter an amount or recipient address.

- Local Storage: The selected team number and token address are stored in localStorage so they persist across page reloads, reducing repetitive input.

- Auto Balance Updates: The DApp watches for Transfer events and automatically refreshes the balance when the connected account is involved in a transfer.

### Issues Encountered and Fixes

- Invalid Teammate Address: At first, one of the teammate addresses copied from the faucet list showed as invalid. I confirmed the formatting and switched to a valid faucet account address to complete the transfer successfully.

- Token Address Confusion: The address 0x5Fbdb… initially appeared in .env (default Hardhat local address). I clarified that the real DIDLab token address comes from the deployment in Activity 3 and updated the config to ensure the DApp points to the correct contract.

- Browser Restrictions: Since browsers block import ... from when using the file:// protocol, I had to serve the DApp through a local HTTP server (Python http.server or npx http-server) to make the module imports work.

These adjustments ensured the DApp worked reliably on the DIDLab Team 10 chain and provided a smoother user experience.
---

## Team Information
- **Team Number:** 10  
- **Partner(s):** Priya Viswanadharao and Lahari  

---

## Network Configuration
- **RPC URL:** `https://hh-10.didlab.org`  
- **Chain ID (hex):** `0x7a72`  
- **Chain ID (decimal):** `31346`  

---

## Token Details
- **Token Name:** CampusCredit  
- **Token Symbol:** CAMP  
- **Decimals:** 18  
- **Token Address:** `0x5Fbdb2315678afecb367f032d93F642f64180aa3`  

---

## Implementation Features
Assignment 4 requirements implemented in this DApp:

1. **Connect Flow**  
   - “Connect & Switch Network” button requests accounts via MetaMask.  
   - Automatically adds/switches to DIDLab Team 10 chain.  

2. **Token Load**  
   - Input for token address.  
   - Reads and displays token metadata (name, symbol, decimals).  
   - Persists token address in `localStorage`.  

3. **Balance View**  
   - Reads connected account’s balance via `balanceOf`.  
   - Displays in human-readable format with decimals.  

4. **Transfer**  
   - Inputs: recipient address + human amount.  
   - Executes `transfer(to, amount)`.  
   - Displays transaction hash, block number, and gas used.  

5. **Updates**  
   - Balance refreshes automatically when Transfer events involve the account.  
   - Manual “Refresh Balance” button provided.  

6. **Wallet Integration**  
   - “Add Token to MetaMask” button integrates CAMP into MetaMask.  

---

## How to Run (Step by Step)

This section explains how **anyone** can run the DApp locally.

### 1. Prerequisites
Ensure the following are installed:
- **Node.js 22.x** (`node -v`)  
- **Python 3.x** (`python3 --version`)  
- **MetaMask browser extension**  

You will also need the DIDLab Team 10 configuration (RPC, Chain ID, Token Address above).  

---

### 2. Clone the Repository
```bash
git clone https://github.com/pviswanadharao/blockchain-assignment4-viswanadharao.git
cd blockchain-assignment4-viswanadharao/didlab-dapp
````

---

### 3. Start a Local Web Server

Browsers block ES Module imports (`import ... from`) over `file://`.
You must run the DApp using a local server.

Choose one of the following options:



```bash
python3 -m http.server 8000
```


```

You should see a message like:

```
Serving HTTP on 0.0.0.0 port 8000 ...
```

---

### 4. Open in Browser

Go to:

```
http://localhost:8000
```

You should now see the **DIDLab — ERC-20 DApp UI**.

---

### 5. Connect MetaMask

1. Click **“1) Connect & Switch Network”**.
2. Approve MetaMask requests to connect your account.
3. MetaMask will prompt to add/switch to Team 10:

   * RPC: `https://hh-10.didlab.org`
   * Chain ID: `31346`
   * Currency Symbol: ETH
4. Approve both add and switch prompts.
5. The DApp will show:

   * Connected account address.
   * Network name & ID.
   * Log message: `Connected. Network ready.`

---

### 6. Load the Token

1. Paste your token address:

   ```
   0x5Fbdb2315678afecb367f032d93F642f64180aa3
   ```
2. Click **“2) Load Token”**.
3. The DApp will display:

   * Token Name: CampusCredit
   * Symbol: CAMP
   * Decimals: 18
   * Token Address
   * Your CAMP balance

---

### 7. Transfer Tokens

1. Enter a recipient address (teammate or self).
2. Enter an amount (e.g., `10`).
3. Click **Send**.
4. MetaMask will prompt → click **Confirm**.
5. Once mined, the DApp will show:

   * Transaction hash
   * Block number
   * Gas used
   * Updated balance

---

### 8. Add Token to MetaMask

1. Click **“Add Token to MetaMask”**.
2. Approve MetaMask popup.
3. CAMP will now appear in MetaMask Assets tab.

---

### 9. Verify Transfer in MetaMask

* Open MetaMask → Activity tab.
* You should see the CAMP transfer.
* Transaction hash matches DApp logs.

---

## Notes

* Added error handling for:

  * Invalid addresses
  * Wrong token address
  * Insufficient balance
* Token address persists in localStorage for convenience.
* Issues encountered: teammate address initially invalid, fixed by using valid faucet addresses.


