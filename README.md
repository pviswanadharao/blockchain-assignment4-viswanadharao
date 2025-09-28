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
### 3. Start a Local Web Server

Browsers do not allow ES Module imports (`import ... from`) directly over `file://`.  
You must serve the HTML using a local web server.  

Choose one of the following options:

#### Option A: Using Python (recommended)
```bash
python3 -m http.server 8000
