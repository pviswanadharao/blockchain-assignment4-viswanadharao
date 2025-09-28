# DIDLab Activity 4 — ERC-20 DApp UI

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

## Implementation Plan

This activity builds a minimal **DApp user interface** to interact with our ERC-20 token deployed in Activity 3.  

### Goals
- Connect to MetaMask and switch to the DIDLab Team 10 network.  
- Load ERC-20 token metadata (name, symbol, decimals).  
- Show current account, network, token details, and balance.  
- Transfer CAMP tokens to another account.  
- Watch for transfer events and update balances automatically.  
- Add CAMP token directly to MetaMask.  

### Steps Completed
1. Created a new folder `didlab-dapp` and added a single file `index.html`.  
2. Configured the DApp with Team 10 RPC, Chain ID, and token address.  
3. Tested the DApp with MetaMask:
   - Connected & switched network.  
   - Loaded CampusCredit (CAMP) token.  
   - Performed transfer of **10 CAMP** to a teammate’s address.  
   - Verified success in DApp log and MetaMask.  
   - Added CAMP token to MetaMask for visibility.  

---



## How to Run (Step by Step)

This section explains how **anyone** can run this project from scratch.

### 1. Prerequisites
Make sure you have the following installed:
- **Node.js 22.x** (check with `node -v`).  
- **Python 3.x** (for simple local server).  
- **MetaMask extension** installed in your browser (Chrome/Firefox).  

You will also need:
- **DIDLab Team 10 network details** (provided above).  
- **Token Address** from your `.env` or deployment logs.  

---

### 2. Clone the Repository
Open a terminal and run:
```bash
git clone https://github.com/pviswanadharao/blockchain-activity4-viswanadharao.git
cd blockchain-activity4-viswanadharao/didlab-dapp

### 3.Start a Local Web Server

Browsers do not allow ES Module imports (import ... from) directly over file://.
You must serve the HTML using a local web server.

Choose one of the following options:

Option A: Using Python (recommended)

If Python 3 is installed, run:

npx http-server -p 8000

If you don’t have it, install it globally first:

npm install -g http-server

You should see a message like:

Serving HTTP on 0.0.0.0 port 8000 ...

4. Open in Browser

Go to:
ou should see the DIDLab — ERC-20 DApp UI.

5. Connect MetaMask

Click the button “1) Connect & Switch Network”.

MetaMask will ask permission to connect your account. Approve it.

MetaMask will then prompt you to add/switch to DIDLab Team 10:

RPC: https://hh-10.didlab.org

Chain ID: 31346

Currency Symbol: ETH

Approve both the add and switch prompts.

The DApp will now display:

Your account address.

Network name and ID.

Confirmation log “Connected. Network ready.”

6. Load the Token

In the Token Address field, paste your token address:
    0x5Fbdb2315678afecb367f032d93F642f64180aa3

    Click “2) Load Token”.

    The DApp will display:

        Token Name: CampusCredit

        Symbol: CAMP

        Decimals: 18

        Token Address (confirmed)

        Your CAMP balance

7. Transfer Tokens

    In the Recipient field, enter an Ethereum address (e.g., your teammate’s address or even your own for a self-transfer).

    In the Amount field, enter the number of CAMP tokens (e.g., 10).

    Click Send.

    MetaMask will open a confirmation window → click Confirm.

    Once the transaction is mined:

        The DApp will log the transaction hash, block number, and gas used.

        Your CAMP balance will update automatically.

        8. Add Token to MetaMask

Click the “Add Token to MetaMask” button.

MetaMask will open a popup to add CAMP.

Approve, and CAMP will now appear in your wallet with your balance.

9. Verify Transfer in MetaMask

Open MetaMask.

Go to Activity tab.

You should see the CAMP transfer you performed.

The transaction hash can be cross-checked in the DApp logs.

Notes

If Connect does nothing → check MetaMask is installed and you are not in private browsing mode.

If Load Token shows “returned no data (0x)” → check that your token address is correct and deployed on DIDLab Team 10.

If Insufficient funds error occurs → ensure you have CAMP tokens from your deployer account (import faucet key if needed).
