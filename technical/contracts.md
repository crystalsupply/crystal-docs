# Smart Contracts Overview

CrystalSupply is built on a suite of smart contracts deployed on the Monad blockchain. All contracts are written in Solidity ^0.8.19 and use OpenZeppelin libraries for security.

## Contract Architecture

```
┌─────────────────────────────────────────────────┐
│         CrystalSupply Ecosystem                 │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌──────────────────┐                          │
│  │  Crystal.sol     │◄────────┐                │
│  │  (TAL Token)     │         │ mint()         │
│  └────────┬─────────┘         │                │
│           │                   │                │
│           │ transfer()  ┌─────┴──────────────┐ │
│           │             │                    │ │
│           ▼             │  CrystalSupply.sol │ │
│  ┌──────────────────┐  │  (Mining Engine)   │ │
│  │ CrystalStaking   │  │                    │ │
│  │ Comp.sol         │◄─┤ - prospect()       │ │
│  │ (Auto-Compound)  │  │ - checkpoint()     │ │
│  └────────┬─────────┘  │ - claim()          │ │
│           │            └─────────┬──────────┘ │
│           │                      │            │
│           │                      │            │
│  ┌────────▼────────┐   ┌────────▼──────────┐ │
│  │  DEX Liquidity  │   │  Pyth Entropy V2  │ │
│  │  Pools          │   │  (VRF Oracle)     │ │
│  └─────────────────┘   └───────────────────┘ │
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

## Security Features

### Access Control

All contracts use OpenZeppelin's `Ownable` for admin functions:

```solidity
// Only owner can set critical parameters
function setMinter(address _minter) external onlyOwner

// Only minter can mint TAL
function mint(address to, uint256 amount) external {
    require(msg.sender == minter, "Not minter");
    // ...
}
```

### Reentrancy Protection

All state-changing functions use `nonReentrant` modifier:

```solidity
function prospect(uint256 roundId, uint8 blockIdx, uint256 amount)
    external
    payable
    nonReentrant
{
    // Safe from reentrancy attacks
}
```

### Integer Overflow Protection

Solidity ^0.8.19 has built-in overflow protection:

```solidity
// Automatically reverts on overflow/underflow
uint256 total = amount1 + amount2;
```

### Input Validation

All functions validate inputs:

```solidity
function prospect(uint256 roundId, uint8 blockIdx, uint256 amount) external {
    require(roundId == currentRoundId, "Invalid round");
    require(blockIdx < GRID_SIZE, "Invalid block");
    require(amount >= MIN_STAKE, "Below minimum");
    require(!isRolling, "Round ended");
    // ...
}
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

## Gas Optimization

### Efficient Data Structures

```solidity
// Packed structs to save storage
struct Round {
    uint256 monTotalOfLosingBlocks;  // 1 slot
    uint256 monTotalOnWinningBlock;  // 1 slot
    uint256 totalRoundStake;         // 1 slot
    uint8 winningBlock;              // \
    bool finalized;                  //  } 1 slot (packed)
    bool motherlodeHit;              // /
    // ...
}
```

### Batch Operations

```solidity
// Keepers can checkpoint multiple rounds at once
function checkpointMultiple(address user, uint256[] calldata roundIds) external {
    for (uint i = 0; i < roundIds.length; i++) {
        _checkpoint(user, roundIds[i]);
    }
}
```

### View Functions

Heavy calculations done in view functions (free):

```solidity
function getCurrentReward() public view returns (uint256) {
    uint256 totalMinted = crystalToken.totalSupply() - INITIAL_CIRCULATING;
    uint256 halvingsPassed = totalMinted / HALVING_INTERVAL;
    if (halvingsPassed >= MAX_HALVINGS) {
        return INITIAL_REWARD / (2 ** MAX_HALVINGS);
    }
    return INITIAL_REWARD / (2 ** halvingsPassed);
}
```

## Events

All contracts emit comprehensive events for off-chain tracking:

### CrystalSupply Events

```solidity
event Prospect(address indexed user, uint256 roundId, uint8 blockIdx, uint256 amount);
event RoundEnded(uint256 roundId, uint8 winBlock, bool winnerTakeAll, bool motherlode);
event CheckpointedByKeeper(address indexed keeper, address indexed user, uint256 roundId, uint256 tokens, uint256 mon, uint256 keeperFee);
event Claimed(address indexed user, uint256 monAmt, uint256 tokenAmt);
event RoundStarted(uint256 indexed roundId, uint256 timestamp);
```

### Crystal Events

```solidity
event MinterUpdated(address indexed oldMinter, address indexed newMinter);
event Transfer(address indexed from, address indexed to, uint256 value);
event Approval(address indexed owner, address indexed spender, uint256 value);
```

### Staking Events

```solidity
event Deposited(address indexed user, uint256 amount, uint256 sharesIssued, uint256 newBalance);
event Withdrawn(address indexed user, uint256 amount, uint256 sharesBurned, uint256 newBalance, uint256 rewardsEarned);
event RewardsDistributed(uint256 amount, uint256 newTotalPooled);
```

## Testing

All contracts should have comprehensive test coverage:

### Unit Tests

```solidity
// test/CrystalSupply.t.sol
function testProspect() public {
    vm.prank(user1);
    crystalSupply.prospect{value: 1 ether}(1, 0, 1 ether);

    assertEq(crystalSupply.userBlockDeposits(1, user1, 0), 1 ether);
}
```

### Integration Tests

```solidity
function testFullMiningRound() public {
    // Users prospect
    // Round ends
    // Randomness received
    // Winners claim rewards
    // Verify balances
}
```

### Fuzzing Tests

```solidity
function testFuzzProspect(uint256 amount) public {
    vm.assume(amount >= MIN_STAKE && amount <= 100 ether);
    // Test with random amounts
}
```

## Audit Status

**Status:** Pending audit

**Scope:**
- Crystal.sol
- CrystalSupply.sol
- CrystalStakingComp.sol
- All associated libraries

**Auditor:** TBD

Check [Audit Reports](../resources/audits.md) for latest status.

## Contract Addresses

**Network:** Monad Mainnet

| Contract | Address |
|----------|---------|
| Crystal (TAL) | `TBD` |
| CrystalSupply | `TBD` |
| CrystalStakingComp | `TBD` |
| ProtocolVault | `TBD` |
| AdminWallet | `TBD` |

See [Contract Addresses](addresses.md) for full list.

## Source Code

All contracts are open source and available on GitHub:

**Repository:** [Coming Soon]

**License:** MIT

**Verified Contracts:** All contracts will be verified on Monad block explorer

## Development

### Building Contracts

```bash
# Install dependencies
npm install

# Compile contracts
npx hardhat compile

# Run tests
npx hardhat test

# Deploy (testnet)
npx hardhat run scripts/deploy.js --network monad-testnet
```

### Local Development

```bash
# Start local node
npx hardhat node

# Deploy locally
npx hardhat run scripts/deploy.js --network localhost

# Run tests
npx hardhat test
```

## Next Steps

Explore detailed documentation for each contract:

- [Crystal Token (TAL)](crystal-token.md)
- [CrystalSupply Contract](crystal-supply.md)
- [Staking Contract](staking-contract.md)
- [Pyth Entropy Integration](entropy.md)

Or dive into:

- [Integration Guide](../advanced/integration.md)
- [Security Considerations](../advanced/security.md)
- [Contract Addresses](addresses.md)
