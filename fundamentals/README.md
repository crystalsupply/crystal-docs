# Protocol Fundamentals

Understanding the core mechanisms that power CrystalSupply.

## Overview

CrystalSupply is built on three fundamental pillars that work together to create a fair, sustainable, and engaging mining ecosystem:

1. **Grid-Based Mining** - A unique 25-block system powered by verifiable randomness
2. **Deflationary Economics** - Bitcoin-inspired halving mechanism with 21M max supply
3. **Auto-Compounding Rewards** - Sustainable value accrual through protocol fees

## What You'll Learn

This section covers the essential concepts you need to understand how CrystalSupply works:

### 🎲 [How Mining Works](mining.md)

Dive deep into the mining mechanism:
- The 25-block grid system
- Round lifecycle and timing
- Pyth Entropy VRF randomness
- Reward distribution formulas
- Winner take all & motherlode modes
- Refined vs unrefined TAL
- Mining economics and expected value

**Perfect for:** Understanding the core gameplay and mining mechanics

### 💎 [Tokenomics](tokenomics.md)

Learn about Crystal (TAL) token economics:
- Supply distribution (100% fair launch)
- Halving schedule (every 3M TAL)
- Fee structure and protocol revenue
- Token utility (staking, governance, value accrual)
- Deflationary mechanisms
- Long-term sustainability model

**Perfect for:** Investors and long-term holders

## Key Concepts

### Fair Launch

CrystalSupply has **zero pre-mine** and **zero team allocation**. Every single TAL token must be mined by the community. This ensures:

✅ No insider advantage
✅ Fair price discovery
✅ Community-driven distribution
✅ Aligned incentives from day one

### Halving Mechanism

Inspired by Bitcoin, TAL emissions halve every 3,000,000 tokens mined:

| Era | Reward | Total Mined |
|-----|--------|-------------|
| 0   | 32 TAL | 3M |
| 1   | 16 TAL | 3M |
| 2   | 8 TAL  | 3M |
| 3   | 4 TAL  | 3M |
| 4   | 2 TAL  | 3M |
| 5   | 1 TAL  | 3M |
| 6   | 0.5 TAL| To max supply |

This creates predictable scarcity and rewards early participants.

### Provably Fair Randomness

Every round uses **Pyth Entropy V2** to select the winning block:

```
Round Ends → Request Randomness → Pyth Generates VRF
→ Callback with Random Number → Winner Determined → Finalize Round
```

This ensures:
- ✅ Unpredictable outcomes
- ✅ Verifiable on-chain
- ✅ Cannot be manipulated
- ✅ Transparent and auditable

### Sustainable Revenue Model

Protocol generates revenue through mining fees:

**Winners pay 11%:**
- 10% → Protocol Vault (buybacks + staking rewards)
- 1% → Admin (development & operations)

**Losers pay 1.1%:**
- 1% → Protocol Vault
- 0.1% → Admin

This creates sustainable funding for:
- TAL buybacks from market
- Auto-compounding staking rewards
- Protocol development and growth
- Long-term ecosystem sustainability

## Quick Stats

| Metric | Value |
|--------|-------|
| **Max Supply** | 21,000,000 TAL |
| **Initial Reward** | 32 TAL per round |
| **Halving Interval** | 3,000,000 TAL |
| **Round Duration** | ~60 seconds |
| **Grid Size** | 25 blocks (5x5) |
| **Min Stake** | 0.1 MON |
| **Blockchain** | Monad (EVM) |

## Why These Fundamentals Matter

Understanding these core concepts helps you:

**As a Miner:**
- Choose optimal blocks and stake amounts
- Calculate expected returns
- Understand risk vs reward
- Plan long-term accumulation strategy

**As a Staker:**
- Evaluate staking APR sustainability
- Understand where rewards come from
- Make informed hold/sell decisions
- Participate in protocol growth

**As an Investor:**
- Assess tokenomics and value accrual
- Understand supply dynamics
- Evaluate long-term sustainability
- Compare to other protocols

## Next Steps

Ready to dive deeper? Explore:

- 📖 [How Mining Works](mining.md) - Complete mining guide
- 💰 [Tokenomics](tokenomics.md) - Economic model details
- 🎯 [Start Mining](../getting-started/quick-start.md) - Begin earning TAL
- 📊 [Staking Guide](../guides/staking.md) - Earn passive rewards

---

*CrystalSupply fundamentals are designed for fairness, sustainability, and long-term value creation.*
