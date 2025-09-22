# Assignment 3 – Short Write-up  

### a. Where I enforced: cap, pause, roles  
- **Cap enforcement:** Implemented in `CampusCreditV2.sol` using OpenZeppelin’s `ERC20Capped`. The `mint` function checks that total supply + new mint ≤ cap.  
- **Pause:** Used OpenZeppelin’s `Pausable`. Only accounts with the `PAUSER_ROLE` can call `pause()` or `unpause()`. All transfers are blocked while paused.  
- **Roles:** Implemented using `AccessControl`.  
  - `DEFAULT_ADMIN_ROLE` → deployer account manages roles.  
  - `MINTER_ROLE` → allows controlled minting and airdrops.  
  - `PAUSER_ROLE` → allows pausing/unpausing the token.  

### b. Why batch airdrop saved gas in my data  
- **Batch Airdrop:** Combined multiple transfers into a single transaction.  
- **Gas Savings Mechanism:**  
  - Used **unchecked loops** to reduce overhead.  
  - Used **custom errors** (`ArrayLengthMismatch`, `CapExceeded`) instead of strings.  
  - Shared calldata and amortized transaction costs across recipients.  
- **Result:** My output showed ~**14.87% gas saved** compared to performing the same transfers individually.  

### c. Issues I faced and how I fixed them  
1. **BigInt conversion error in airdrop script** → Fixed by properly using `parseUnits("10", 18)` instead of passing raw BigInt.  
2. **MetaMask setup confusion** → Initially tried on local Hardhat network; later corrected to use my professor’s live DIDLab endpoint (`https://hh-10.didlab.org`, Chain ID `31346`).  
3. **GitHub pushes rejected** → Fixed by pulling with `--rebase` before pushing and ensuring `.env` is excluded.  
4. **Token not visible in MetaMask** → Resolved by importing the deployed `TOKEN_ADDRESS` manually.  
