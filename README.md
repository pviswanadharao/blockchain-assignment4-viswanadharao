# Assignment 3 (Production-Style ERC-20 on DIDLab (Hardhat v3 + Viem)

## Overview
This repository contains my implementation for Activity 3 of the Blockchain Lab.
The assignment required creating a production-style ERC-20 token on the DIDLab network using Hardhat v3, Viem, and OpenZeppelin v5, with features like capped supply, pausable transfers, role-based access control, and a gas-aware batch airdrop.

---

## Steps Completed

### 1. Project Setup
-Environment

Node.js: v22.x
Hardhat: v3 (ESM mode, "type": "module" in package.json)
Client library: Viem
Contracts: OpenZeppelin v5
Network: DIDLab Team 10
RPC URL: https://hh-10.didlab.org
Chain ID: 31346
Private key: Faucet key provided by professor (not real wallet)

###Token Deployment Info

Token Name: CampusCredit
Symbol: CAMP
Cap: 2,000,000 CAMP
Initial Mint: 1,000,000 CAMP
Deployment Output:
TOKEN_ADDRESS: 0x5fbdb2315678afecb367f032d93f642f64180aa3
Deploy Block: 1
Roles Granted:
DEFAULT_ADMIN_ROLE → 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
MINTER_ROLE → 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
PAUSER_ROLE → 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266

###Project Structure
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
ConsoleOutputs/
Screenshots/

Scripts & Outputs

1. Deploy (scripts/deploy.ts)
Deploys the ERC-20 contract using .env parameters.
Console output includes: deploy tx hash, contract address, block number.

2. Transfer & Approve (scripts/transfer-approve.ts)
Prints balances (before/after) for two accounts.
Executes transfer and approve, then shows allowance.
Console output includes: tx hash, gas used, balances before/after, allowance.

3. Batch Airdrop vs Singles (scripts/airdrop.ts)
Performs batch airdrop and equivalent N single transfers.
Prints gas used for both and % gas saved.

Sample Output:
Airdrop: ... gasUsed: 118879
Singles total gasUsed: 139636
Batch saved ≈ 14.87% gas vs singles


Logs & Events (scripts/logs-query.ts)
Queries last ~2000 blocks for Transfer, Approval, and RoleGranted events.
Prints block numbers + arguments for each event.

MetaMask Integration
Custom Network:
Network Name: DIDLab Team 10
RPC URL: https://hh-10.didlab.org
Chain ID: 31346
Currency Symbol: ETH
Imported Faucet Account using provided private key.
Imported CAMP Token using deployed TOKEN_ADDRESS.
Sent CAMP transfer in MetaMask, transaction hash recorded.

Gas-aware Airdrop Note
The batch airdrop implementation is more efficient than multiple single transfers because:
Uses custom errors (CapExceeded, ArrayLengthMismatch) instead of generic reverts.
Uses unchecked loops to save gas
Reduces calldata and amortizes transaction overhead into a single tx.
Achieved ~14.87% gas savings in tests.

(Screenshots)
Custom DIDLab Team 10 network in MetaMask.
CAMP token imported with balance visible.
CAMP transfer tx details page (hash shown).
Console outputs for Deploy, Transfer+Approve, Airdrop, Logs (saved in ConsoleOutputs/).

Notes
.env is excluded from GitHub for security (only .env.example included).
Used Node.js v22.x as required.
All requirements (cap enforcement, pausable transfers, role gating, airdrop revert reasons) tested successfully.
