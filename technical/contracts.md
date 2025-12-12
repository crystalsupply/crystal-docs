# Smart Contracts Overview

CrystalSupply is built on a suite of smart contracts deployed on the Monad blockchain. All contracts are written in Solidity ^0.8.19 and use OpenZeppelin libraries for security.

## Contract Architecture

```
┌─────────────────────────────────────────────────┐
│         CrystalSupply Ecosystem                 │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌──────────────────┐                           │
│  │  Crystal.sol     │◄────────┐                 │
│  │  (TAL Token)     │         │ mint()          │
│  └────────┬─────────┘         │                 │
│           │                   │                 │
│           │ transfer()  ┌─────┴──────────────┐  │
│           │             │                    │  │
│           ▼             │  CrystalSupply.sol │  │
│  ┌──────────────────┐  │  (Mining Engine)   │   │
│  │ CrystalStaking   │  │                    │   │
│  │ Comp.sol         │◄─┤ - prospect()       │   │
│  │ (Auto-Compound)  │  │ - checkpoint()     │   │
│  └────────┬─────────┘  │ - claim()          │   │
│           │            └─────────┬──────────┘   │
│           │                      │              │
│           │                      │              │
│  ┌────────▼────────┐   ┌────────▼──────────┐    │
│  │  DEX Liquidity  │   │  Pyth Entropy V2  │    │
│  │  Pools          │   │  (VRF Oracle)     │    │
│  └─────────────────┘   └───────────────────┘    │
│                                                 │
└─────────────────────────────────────────────────┘
```

## Core Contracts

### 1. Crystal.sol (TAL Token)

**Purpose:** ERC20 token with controlled minting

**Key Features:**
- Fixed max supply: 21,000,000 TAL
- Only minter (CrystalSupply) can mint
- Anyone can burn their own tokens
- Standard ERC20 with 18 decimals

**Important Functions:**
```solidity
function mint(address to, uint256 amount) external
function burn(uint256 amount) external
function remainingSupply() external view returns (uint256)
```

**State Variables:**
```solidity
uint256 public constant MAX_SUPPLY = 21_000_000 ether;
address public minter;
```

[Read Full Documentation](crystal-token.md)

### 2. CrystalSupply.sol (Mining Engine)

**Purpose:** Main mining protocol logic

**Key Features:**
- 25-block grid mining system
- Pyth Entropy V2 integration for VRF
- Round-based gameplay (~60s rounds)
- Halving mechanism (every 3M TAL)
- Fee distribution to vault and admin
- Keeper-assisted checkpointing

**Important Functions:**
```solidity
// Mining
function prospect(uint256 roundId, uint8 blockIdx, uint256 amount) external payable
function endRound() external
function startNewRound() external

// Rewards
function checkpoint(address user, uint256 roundId) external
function claimToken(uint256 amount) external
function claimMon(uint256 amount) external

// Admin
function setProtocolVault(address _vault) external
function setKeeperFee(uint256 _fee) external
function setRoundDuration(uint256 _duration) external
```

**State Variables:**
```solidity
uint256 public constant INITIAL_REWARD = 32 ether;
uint256 public constant HALVING_INTERVAL = 3_000_000 ether;
uint256 public constant GRID_SIZE = 25;
uint256 public constant MIN_STAKE = 0.1 ether;

uint256 public currentRoundId;
uint256 public accumulatedTokenPot;
bool public isRolling;

mapping(uint256 => Round) public rounds;
mapping(uint256 => mapping(address => mapping(uint8 => uint256))) public userBlockDeposits;
```

[Read Full Documentation](crystal-supply.md)

### 3. CrystalStakingComp.sol (Auto-Compounding Staking)

**Purpose:** Auto-compounding staking for TAL tokens

**Key Features:**
- Shares-based model (like Lido stETH)
- Automatic reward compounding
- No lock-up period
- Real-time balance updates
- Reward distributor system

**Important Functions:**
```solidity
function deposit(uint256 amount) external
function withdraw(uint256 amount) external
function balanceOf(address user) external view returns (uint256)
function distributeRewards(uint256 amount) external
```

**State Variables:**
```solidity
uint256 public totalShares;
uint256 public totalPooledTokens;
uint256 public totalRewardsDistributed;

mapping(address => uint256) public shares;
mapping(address => uint256) public initialDeposits;
mapping(address => bool) public rewardDistributors;
```

[Read Full Documentation](staking-contract.md)

### 4. Pyth Entropy V2 (External)

**Purpose:** Verifiable randomness for fair mining

**Integration:**
- CrystalSupply requests randomness at round end
- Entropy generates verifiable random number
- Callback determines winning block
- Fully transparent and auditable

**Key Functions Used:**
```solidity
function requestRandomness(bytes32 userCommitment) external payable returns (uint64 sequenceNumber)
function entropyCallback(uint64 sequenceNumber, bytes32 randomNumber) external
```

[Read Full Documentation](entropy.md)

## Contract Relationships

### Minting Flow

```
CrystalSupply.sol
    │
    │ Round ends, rewards calculated
    │
    ├─► mint(winner, rewardAmount)
    │        │
    │        ▼
    │   Crystal.sol
    │        │
    │        └─► _mint(winner, rewardAmount)
    │                 │
    │                 └─► Winner receives TAL
```

### Staking Flow

```
User
  │
  ├─► approve(stakingContract, amount)
  │
  └─► deposit(amount)
        │
        ▼
  CrystalStakingComp.sol
        │
        ├─► transferFrom(user, this, amount)
        │
        └─► Mint shares to user
              │
              └─► Auto-compound rewards over time
```

### Randomness Flow

```
CrystalSupply.sol
  │
  ├─► entropy.requestRandomness(userCommit, fee)
  │        │
  │        └─► Pyth Entropy V2
  │                 │
  │                 └─► Generate verifiable randomness
  │                          │
  │                          └─► entropyCallback(seq, randomNumber)
  │                                   │
  └─◄─────────────────────────────────┘
        │
        └─► Finalize round with winning block
```

## Upgradability

CrystalSupply contracts are **NOT upgradeable**. This design choice ensures:

✅ **Immutability**: Code cannot be changed after deployment
✅ **Trust**: Users know exactly what code is running
✅ **Security**: No admin backdoors or upgrade risks
✅ **Transparency**: What you see is what you get

### Implications

- **Bug Fixes**: Must deploy new version if critical bug found
- **Feature Additions**: New features require new contract deployments
- **Migration**: Users would need to migrate to new contracts

This trade-off prioritizes security and decentralization over flexibility.