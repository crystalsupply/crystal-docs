# Technical Reference

Deep technical documentation for developers, integrators, and advanced users.

## Overview

This section provides comprehensive technical documentation for understanding and integrating with CrystalSupply's smart contracts and infrastructure.

## Documentation

### 📜 [Smart Contracts](contracts.md)

**Complete smart contract architecture and implementation details**

Covers:
- Contract architecture overview
- Core contract descriptions (Crystal, CrystalSupply, CrystalStakingComp)
- State variables and data structures
- Function signatures and usage
- Events and logging
- Security features and access control
- Gas optimization techniques
- Testing and deployment

**Who it's for:** Developers, auditors, and advanced users

**What you'll learn:**
- How the contracts work together
- Security mechanisms in place
- Integration points for developers
- Contract upgrade strategy (immutable)

### 🏠 [Contract Addresses](addresses.md)

**Official deployed contract addresses on Monad**

Includes:
- Crystal Token (TAL)
- CrystalSupply (Mining)
- CrystalStakingComp (Staking)
- CrystalBuyback
- Protocol Vault
- Admin Wallet

**Who it's for:** Everyone integrating with CrystalSupply

**Use cases:**
- Adding TAL to wallets
- Integrating with DEX aggregators
- Building analytics tools
- Verifying contract interactions

### 📖 [Glossary](glossary.md)

**Comprehensive terminology reference**

Definitions for:
- Protocol-specific terms
- Blockchain concepts
- Mining terminology
- Staking mechanics
- Technical jargon

**Who it's for:** Anyone learning about CrystalSupply

**Use cases:**
- Understanding documentation
- Learning new concepts
- Quick reference lookup
- Explaining to others

## For Developers

### Quick Start Integration

**Add TAL to your dApp:**

```javascript
// TAL Token Contract
const TAL_ADDRESS = '0x126e7B338D242c9B9D03d6243b9f501d137d3F58';

// Get user's TAL balance
const talContract = new ethers.Contract(TAL_ADDRESS, ERC20_ABI, provider);
const balance = await talContract.balanceOf(userAddress);
```

**Interact with staking:**

```javascript
// Staking Contract
const STAKING_ADDRESS = '0xD33F0c3a9B4B675893Bf297827C60e793878494e';

// Check user's staked balance
const stakingContract = new ethers.Contract(STAKING_ADDRESS, STAKING_ABI, signer);
const stakedBalance = await stakingContract.balanceOf(userAddress);
```

**Monitor mining rounds:**

```javascript
// Mining Contract
const MINING_ADDRESS = '0x0C37B4c1e658ab0E812b66c3D9884963097176a2';

// Get current round info
const miningContract = new ethers.Contract(MINING_ADDRESS, MINING_ABI, provider);
const currentRound = await miningContract.currentRoundId();
const roundInfo = await miningContract.rounds(currentRound);
```

### Available ABIs

All contract ABIs are available:
- In the verified contracts on Monad Explorer
- In the GitHub repository (coming soon)
- Via the CrystalSupply SDK (coming soon)

### Common Integration Patterns

**Display TAL Price:**
```javascript
// Get TAL price from DEX
const pairAddress = await factory.getPair(TAL_ADDRESS, MON_ADDRESS);
const pair = new ethers.Contract(pairAddress, PAIR_ABI, provider);
const reserves = await pair.getReserves();
const talPrice = reserves[1] / reserves[0]; // MON per TAL
```

**Check Mining Eligibility:**
```javascript
// Check if round is active
const isRolling = await miningContract.isRolling();
const roundId = await miningContract.currentRoundId();

if (!isRolling) {
  // Round is active, user can prospect
  console.log(`Round ${roundId} is accepting prospects`);
}
```

**Calculate Staking APR:**
```javascript
// Get staking metrics
const totalPooled = await stakingContract.totalPooledTokens();
const totalShares = await stakingContract.totalShares();
const sharePrice = totalPooled / totalShares;

// Calculate APR based on recent rewards
const rewardsDistributed = await stakingContract.totalRewardsDistributed();
// Implement your APR calculation logic
```

## Architecture Diagrams

### System Overview

```
┌─────────────────────────────────────────────┐
│         CrystalSupply Protocol              │
├─────────────────────────────────────────────┤
│                                             │
│  ┌──────────────────┐                      │
│  │  Crystal (TAL)   │◄──────┐              │
│  │  ERC20 Token     │       │ mint()       │
│  └────────┬─────────┘       │              │
│           │                 │              │
│           │ transfer() ┌────┴─────────────┐│
│           │            │                  ││
│           ▼            │ CrystalSupply    ││
│  ┌──────────────────┐ │ (Mining)         ││
│  │ CrystalStaking   │ │                  ││
│  │ Comp             │◄┤ - prospect()     ││
│  │ (Auto-Compound)  │ │ - checkpoint()   ││
│  └────────┬─────────┘ │ - claim()        ││
│           │           └─────────┬────────┘│
│           │                     │         │
│  ┌────────▼────────┐  ┌────────▼────────┐│
│  │ CrystalBuyback  │  │ Pyth Entropy    ││
│  │                 │  │ (VRF)           ││
│  └─────────────────┘  └─────────────────┘│
│                                            │
└────────────────────────────────────────────┘
```

### Mining Flow

```
User → prospect() → CrystalSupply
                         ↓
                    Round Ends
                         ↓
                Request Randomness → Pyth Entropy
                         ↓
                Generate VRF Random Number
                         ↓
                Callback with Random
                         ↓
                Determine Winner
                         ↓
                Finalize Round
                         ↓
        ┌────────────────┴─────────────┐
        ↓                              ↓
   Mint TAL                      Refund MON
        ↓                              ↓
  Winners Receive                 All Users
```

### Staking Flow

```
User → approve() → TAL Token
         ↓
    deposit() → CrystalStakingComp
         ↓
    Mint Shares
         ↓
    ┌─────────────────┐
    │ Auto-Compound   │
    │ Rewards         │
    └────────┬────────┘
             ↓
    Share Value Increases
             ↓
    User Balance Grows Automatically
             ↓
    withdraw() → Receive TAL + Rewards
```

## Security

### Audit Status

**Current Status:** Pending audit

**Planned Audits:**
- Smart contract security audit
- Economic model review
- Formal verification (critical functions)

**Bug Bounty:** Coming soon

### Security Features

All contracts implement:
- ✅ OpenZeppelin libraries (battle-tested)
- ✅ ReentrancyGuard on state-changing functions
- ✅ Access control (Ownable)
- ✅ Input validation
- ✅ Overflow protection (Solidity ^0.8.19)
- ✅ No upgradability (immutable contracts)

### Best Practices for Integrators

When integrating with CrystalSupply:

1. **Always verify contract addresses** from official sources
2. **Use latest ABIs** from verified contracts
3. **Handle errors gracefully** (reverts, timeouts)
4. **Implement proper gas estimation**
5. **Test on testnet first** before mainnet
6. **Monitor events** for state changes
7. **Respect rate limits** on RPC calls
8. **Cache static data** (contract addresses, etc.)

## Development Tools

### Recommended Stack

- **Language:** Solidity ^0.8.19
- **Framework:** Hardhat or Foundry
- **Library:** ethers.js v6 or viem
- **Testing:** Mocha + Chai
- **Network:** Monad RPC

### Useful Libraries

```bash
# ethers.js for contract interaction
npm install ethers

# For React dApps
npm install @rainbow-me/rainbowkit wagmi viem

# For analytics
npm install @uniswap/sdk-core @uniswap/v2-sdk
```

### Example Projects

Coming soon:
- CrystalSupply SDK (JavaScript/TypeScript)
- React integration example
- Analytics dashboard template
- Keeper bot reference implementation

## API Reference

### CrystalSupply (Mining)

**Read Functions:**
```solidity
function currentRoundId() external view returns (uint256)
function rounds(uint256 roundId) external view returns (Round memory)
function userBlockDeposits(uint256 roundId, address user, uint8 blockIdx) external view returns (uint256)
function getCurrentReward() external view returns (uint256)
function isRolling() external view returns (bool)
```

**Write Functions:**
```solidity
function prospect(uint256 roundId, uint8 blockIdx, uint256 amount) external payable
function checkpoint(address user, uint256 roundId) external
function claimToken(uint256 amount) external
function claimMon(uint256 amount) external
```

### CrystalStakingComp (Staking)

**Read Functions:**
```solidity
function balanceOf(address user) external view returns (uint256)
function shares(address user) external view returns (uint256)
function totalPooledTokens() external view returns (uint256)
function totalShares() external view returns (uint256)
```

**Write Functions:**
```solidity
function deposit(uint256 amount) external
function withdraw(uint256 amount) external
```

### Crystal (TAL Token)

**Standard ERC20:**
```solidity
function balanceOf(address account) external view returns (uint256)
function transfer(address to, uint256 amount) external returns (bool)
function approve(address spender, uint256 amount) external returns (bool)
function transferFrom(address from, address to, uint256 amount) external returns (bool)
function allowance(address owner, address spender) external view returns (uint256)
```

**Custom Functions:**
```solidity
function burn(uint256 amount) external
function remainingSupply() external view returns (uint256)
function MAX_SUPPLY() external view returns (uint256)
```

## Support

**For Developers:**
- 💻 GitHub Issues (coming soon)
- 💬 Discord #dev-chat
- 📧 Email: dev@crystalsupply.xyz (coming soon)
- 📚 SDK Documentation (coming soon)

**For Integrators:**
- 🤝 Partnership inquiries
- 🔌 Integration support
- 📊 API access
- 🎨 Brand assets

---

Ready to build? Check out the [Smart Contracts](contracts.md) documentation or view [Contract Addresses](addresses.md) to get started!
