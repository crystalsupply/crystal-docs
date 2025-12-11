# How Mining Works

CrystalSupply uses a unique grid-based mining system powered by provable randomness to distribute TAL tokens fairly to participants.

## Mining Overview

Unlike traditional Proof-of-Work mining that requires expensive hardware, CrystalSupply mining is accessible to anyone with:
- A Web3 wallet
- MON tokens (Monad's native currency)
- Internet connection

## The 25-Block Grid

Every mining round uses a **5x5 grid** with 25 blocks (numbered 0-24):

```
┌─────┬─────┬─────┬─────┬─────┐
│  0  │  1  │  2  │  3  │  4  │
├─────┼─────┼─────┼─────┼─────┤
│  5  │  6  │  7  │  8  │  9  │
├─────┼─────┼─────┼─────┼─────┤
│ 10  │ 11  │ 12  │ 13  │ 14  │
├─────┼─────┼─────┼─────┼─────┤
│ 15  │ 16  │ 17  │ 18  │ 19  │
├─────┼─────┼─────┼─────┼─────┤
│ 20  │ 21  │ 22  │ 23  │ 24  │
└─────┴─────┴─────┴─────┴─────┘
```

### Prospecting Blocks

Miners stake MON tokens on one or more blocks. This action is called "prospecting":

```solidity
// Prospecting on block 12 with 1 MON
prospect(roundId: 1, blockIndex: 12, amount: 1 ether)
```

**Key Rules:**
- Minimum stake: 0.1 MON per block
- No maximum stake (stake as much as you want)
- Can prospect multiple blocks in the same round
- Each user can prospect the same block multiple times

## Round Lifecycle

Each mining round follows a strict lifecycle:

### 1. Active Phase (~60 seconds)

```
Round Status: ACTIVE
Time Remaining: 60s → 0s

Miners can:
✅ Prospect new blocks
✅ Add more to existing blocks
✅ View grid statistics
```

During this phase:
- Miners select blocks and stake MON
- Grid fills up with participants
- Total stake per block accumulates
- Round timer counts down

### 2. Intermission Phase (~12 seconds)

```
Round Status: INTERMISSION
Time Remaining: 12s → 0s

Actions:
🔒 Prospecting disabled
🎲 Requesting randomness from Pyth Entropy
⏳ Waiting for VRF callback
```

During intermission:
- No new prospecting allowed
- Smart contract requests random number from Pyth Entropy
- System prepares to finalize round
- Results not yet known

### 3. Finalization

```
Round Status: FINALIZED

Results:
🎯 Winning block revealed
💰 Rewards calculated
📊 Round statistics updated
```

Once Pyth Entropy returns randomness:
- Winning block is determined
- TAL rewards are calculated
- MON stakes become claimable
- New round begins automatically

### 4. Checkpoint Period

```
Miners can now:
✅ Checkpoint rewards (manual or keeper)
✅ Claim TAL tokens
✅ Claim MON refunds
✅ View round history
```

Rewards are available to claim, and miners can:
- Manually checkpoint and claim
- Let keepers auto-checkpoint for a small fee
- Review past round results

## Randomness: Pyth Entropy V2

CrystalSupply uses **Pyth Entropy V2** for provably fair randomness.

### How It Works

```
1. Round ends → Contract requests random number
2. Pyth Entropy generates verifiable randomness
3. Random number used to select winning block (0-24)
4. Results are transparent and verifiable on-chain
```

### Why Pyth Entropy?

✅ **Verifiable**: Anyone can verify the random number
✅ **Unpredictable**: Cannot be manipulated or predicted
✅ **Decentralized**: No single point of failure
✅ **Fast**: Low latency for quick round finalization

### Technical Details

```solidity
// Request randomness
uint64 sequenceNumber = entropy.requestRandomness(
    userRandomNumber,
    feeAmount
);

// Entropy calls back with random number
function entropyCallback(
    uint64 sequenceNumber,
    bytes32 randomNumber
) external {
    // Determine winning block
    uint8 winningBlock = uint8(uint256(randomNumber) % 25);
    // Finalize round...
}
```

## Reward Distribution

### Basic Formula

If your block wins, you receive a share of the round's TAL reward based on:

```
Your TAL Reward = (Your MON Stake / Total MON on Winning Block) × Round TAL Reward
```

### Example Scenario

**Round 100:**
- Current reward: 32 TAL
- Winning block: #12
- Total MON on block 12: 100 MON

**You staked: 10 MON on block 12**

```
Your share = 10 / 100 = 10%
Your reward = 32 TAL × 10% = 3.2 TAL
```

### Winner Take All (Rare)

Occasionally (~1% chance), a round becomes "Winner Take All":

- Only the winning block participants get rewards
- ALL the TAL goes to the winning block
- Losing blocks get full MON refunds (minus small fee)
- Much higher rewards for winners

This adds excitement and variance to the mining experience!

## Motherlode (Very Rare)

Even rarer (~0.1% chance), a "Motherlode" can occur:

- Massive bonus TAL rewards
- Extra incentive for winners
- Creates jackpot-style excitement

## Stake Refunds

### If You Win

When your block wins:
- **TAL Reward**: You earn TAL tokens ✅
- **MON Refund**: You get 89% of your MON back
- **Protocol Fee**: 11% fee taken
  - 10% → Vault (buybacks + staking)
  - 1% → Admin (development)

```
Example: You staked 10 MON
- TAL earned: [Based on your share]
- MON refund: 8.9 MON
- Protocol fee: 1.1 MON (10% + 1%)
```

### If You Lose

When your block doesn't win:
- **No TAL**: You don't earn TAL this round ❌
- **MON Refund**: You get 98.9% of your MON back ✅
- **Small Fee**: 1.1% fee taken
  - 1% → Vault
  - 0.1% → Admin

```
Example: You staked 10 MON
- TAL earned: 0
- MON refund: 9.89 MON
- Protocol fee: 0.11 MON (1% + 0.1%)
```

This means **losing doesn't hurt much**! You get almost all your MON back.

## Refined vs. Unrefined TAL

When you earn TAL from mining, it comes in two forms:

### 1. Refined TAL (Immediate)

- **Available immediately** after checkpoint
- Can be claimed right away
- **No refining fee** if you wait
- **10% refining fee** if claimed before cooldown
- Encourages patience and reduces sell pressure

### 2. Unrefined TAL (Accumulating)

- Accumulates in your miner account
- Refines over time automatically
- No fee after refining period
- Becomes claimable refined TAL

### Strategic Considerations

**Claim Immediately:**
- Pay 10% refining fee
- Get TAL now
- Good if TAL price is pumping

**Wait for Refining:**
- Pay no fee
- Get full amount
- Patient approach
- Better long-term

## Mining Statistics

The protocol tracks various statistics per round:

### Round-Level Stats

```solidity
struct Round {
    uint256 totalRoundStake;        // Total MON staked
    uint256 monTotalOnWinningBlock; // MON on winner
    uint8 winningBlock;             // Which block won
    bool finalized;                 // Is round done?
    bool motherlodeHit;             // Jackpot?
    bool isWinnerTakeAll;           // WTA mode?
    uint256[25] blockTotals;        // MON per block
    uint256[25] minerCounts;        // Miners per block
}
```

### User-Level Stats

```solidity
// How much you staked on each block
userBlockDeposits[roundId][user][blockIndex]

// Your cumulative position at start
userCumulativeStart[roundId][user][blockIndex]

// Your total unclaimed TAL
totalUnclaimedTokens
```

## Mining Economics

### Expected Value (EV) Calculation

Since each block has a 1/25 chance of winning:

```
EV per round = (Reward / 25) - Fees

Example with 32 TAL reward:
- Expected TAL: 32 / 25 = 1.28 TAL
- Minus fees: ~1.1% on average
- Net EV: ~1.27 TAL per round (if staking equal to 1/25 of pool)
```

### Variance

Mining has high variance:
- Most rounds you'll lose (24/25 = 96% chance)
- When you win, you earn big
- Over many rounds, EV converges to average

### Strategy Implications

**High Risk, High Reward:**
- Stake large on few blocks
- Win big or lose big
- High variance

**Low Risk, Steady Gains:**
- Stake small on many blocks
- More consistent results
- Lower variance

**Balanced Approach:**
- Moderate stakes on several blocks
- Medium variance
- Good for most miners

## Accumulating Rewards

### Token Pot Mechanism

The protocol maintains an "accumulated token pot":

```
Token Pot = Unmined TAL from previous rounds
```

If a round has:
- Very few participants
- Winner Take All mode active
- Motherlode triggered

The pot can accumulate and create larger rewards in future rounds!

### Pot Distribution

When pot exists:
- Added to current round reward
- Increases incentive to mine
- Creates interesting dynamics

## Anti-Gaming Mechanisms

CrystalSupply prevents manipulation through:

### 1. Verifiable Randomness

- Pyth Entropy cannot be predicted
- No way to game the winning block
- Fair for all participants

### 2. Minimum Participants

- Configurable minimum (default: 1)
- Prevents empty round abuse
- Can be adjusted by governance

### 3. Round Duration Limits

- Minimum round duration: 60 seconds
- Prevents rapid-fire manipulation
- Gives everyone fair chance to participate

### 4. Fee Structure

- Winners pay 11% fee
- Losers pay 1.1% fee
- Makes spam attacks unprofitable

## Advanced: Keeper System

Keepers are automated bots that checkpoint rewards for users:

### How Keepers Work

```
1. Monitor for finalized rounds
2. Identify users with unclaimed rewards
3. Call checkpoint on their behalf
4. Charge small keeper fee (0.1 MON default)
5. User's rewards are auto-processed
```

### Benefits of Keepers

✅ Automatic reward processing
✅ Saves you gas fees
✅ Batches multiple rounds
✅ Convenient for active miners

### Keeper Fees

- Default: 0.1 MON per checkpoint
- Configurable by protocol
- Paid from your MON refunds
- Optional (you can claim manually)

Learn more in the [Keeper Operations Guide](../advanced/keepers.md).

## Next Steps

Now that you understand how mining works:

- [Learn Mining Strategies](../guides/strategy.md)
- [Understand Round System](rounds.md)
- [Review Tokenomics](tokenomics.md)
- [Start Mining](../guides/mining.md)

## Summary

CrystalSupply mining is:

✅ **Fair**: Provable randomness via Pyth Entropy
✅ **Accessible**: Only need MON tokens
✅ **Transparent**: All data on-chain
✅ **Exciting**: Winner take all & motherlode modes
✅ **Low Risk**: Get most MON back even if you lose
✅ **Rewarding**: Earn TAL tokens for participation

Start mining today! 💎⛏️
