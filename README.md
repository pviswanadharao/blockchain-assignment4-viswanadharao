# Activity 3 — Build, Deploy & Operate a Production-Style ERC-20 on DIDLab

## Overview
This repository contains my implementation for **Activity 3** of the Blockchain lab.  
The activity involved scaffolding a Hardhat v3 project, writing a gas-aware ERC-20 token contract, deploying it to a local DIDLab network, and interacting with it using scripts and MetaMask.  

---

## Steps Completed

### 1. Project Setup
- Initialized a Hardhat v3 project with **Viem** and **TypeScript**.
- Installed dependencies: `hardhat`, `@openzeppelin/contracts`, `viem`, `dotenv`.
- Created and configured `.env` for local Hardhat network (RPC, Chain ID, Private Key).

### 2. Contract Implementation
- Implemented **CampusCreditV2.sol** with:
  - **Cap enforcement** on mint
  - **Pausable** transfers
  - **Role-based access** (ADMIN, MINTER, PAUSER)
  - **Batch airdrop** (gas-aware, unchecked loops, custom errors)
- Location: `contracts/CampusCreditV2.sol`.

### 3. Deployment
- Wrote deploy script (`scripts/deploy.ts`).
- Deployed CampusCreditV2 to **local Hardhat blockchain**:
- Added `TOKEN_ADDRESS` to `.env`.

### 4. Interactions
- **Transfer & Approve (`scripts/transfer-approve.ts`)**
- Successfully transferred `100 CAMP` and approved `50 CAMP`.
- Console Output:
  ```
  Before | Me: 1000000 CAMP | You: 1000000 CAMP
  transfer tx: 0xdf88b1... gasUsed: 29224
  approve tx: 0xaac67a... gasUsed: 46409
  allowance: 50 CAMP
  After | Me: 1000000 CAMP | You: 1000000 CAMP
  ```

- **Batch Airdrop (`scripts/airdrop.ts`)**
- Performed a batch airdrop of `10 CAMP`.
- Gas comparison output:
  ```
  Airdrop: ... gasUsed: 118879
  Singles total gasUsed: 139636
  Batch saved ≈ 14.87% gas vs singles
  ```

- **Logs & Events (`scripts/logs-query.ts`)**
- Queried logs for `Transfer`, `Approval`, and `RoleGranted`.
- Verified deployment, transfers, approvals, and airdrop events.

### 5. MetaMask Integration
- Added **Local DIDLab** network:
- RPC URL: `http://127.0.0.1:8545`
- Chain ID: `31337`
- Currency Symbol: ETH
- Imported deployer account (private key from Hardhat node).
- Imported CAMP token manually using `TOKEN_ADDRESS`.

---

## Results & Learnings
- **ERC-20 Cap + Pausable + Roles** implemented correctly.
- **Gas-aware batch airdrop** showed measurable gas savings (~14.87%).
- Verified **transfer, approve, allowance** workflows.
- Confirmed all events in logs (`Transfer`, `Approval`, `RoleGranted`).
- MetaMask successfully connected to local DIDLab and CAMP token added.

---

## Screenshots (to be added)
- [ ] MetaMask with **Local DIDLab network**.
- [ ] MetaMask showing **CAMP token** balance.
- [ ] Console output of **airdrop.ts** (batch vs singles).
- [ ] Console output of **transfer-approve.ts**.

---

## Project Structure
contracts/
  CampusCreditV2.sol
scripts/
  deploy.ts
  transfer-approve.ts
  airdrop.ts
  logs-query.ts
hardhat.config.ts
.env.example
README.md



---

## Notes
- Used Node.js v22.x (required by Hardhat v3).
- Excluded `.env` from GitHub for security.
- All tests run successfully on local DIDLab chain.

