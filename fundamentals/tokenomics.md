# Tokenomics

Crystal (TAL) is designed with a deflationary, Bitcoin-inspired economic model that ensures fair distribution and long-term sustainability.

## Supply Overview

| Parameter | Value |
|-----------|-------|
| **Token Name** | Crystal |
| **Ticker** | TAL |
| **Max Supply** | 21,000,000 TAL |
| **Decimals** | 18 |
| **Initial Circulating** | 0 TAL |
| **Blockchain** | Monad (EVM) |

## Supply Distribution

```
Total Supply: 21,000,000 TAL

┌────────────────────────────────┐
│     100% Community Mined       │
│                                │
│  No Pre-mine                   │
│  No Team Allocation            │
│  No Investor Rounds            │
│  No Private Sales              │
└────────────────────────────────┘
```

### Fair Launch

**100% of TAL supply must be mined by the community.** There is:

- ❌ No pre-mine
- ❌ No team allocation
- ❌ No investor rounds
- ❌ No airdrops
- ✅ Pure fair launch

## Emission Schedule

CrystalSupply uses a **halving mechanism** inspired by Bitcoin to create scarcity over time.

### Halving Parameters

| Parameter | Value |
|-----------|-------|
| **Initial Reward** | 32 TAL per round |
| **Halving Interval** | Every 3,000,000 TAL minted |
| **Max Halvings** | 6 |
| **Final Reward** | 0.5 TAL per round |

### Halving Schedule

| Halving Era | Reward per Round | Total TAL Minted | Cumulative Supply |
|-------------|------------------|------------------|-------------------|
| **Epoch 0** | 32 TAL | 3,000,000 | 3,000,000 |
| **Epoch 1** | 16 TAL | 3,000,000 | 6,000,000 |
| **Epoch 2** | 8 TAL | 3,000,000 | 9,000,000 |
| **Epoch 3** | 4 TAL | 3,000,000 | 12,000,000 |
| **Epoch 4** | 2 TAL | 3,000,000 | 15,000,000 |
| **Epoch 5** | 1 TAL | 3,000,000 | 18,000,000 |
| **Epoch 6** | 0.5 TAL | Until max supply | 21,000,000 |

### Visual Emission Curve

```
Reward (TAL)
   32 │██████████
      │          ██████████
   16 │                    ██████████
      │                              ██████████
    8 │                                        ██████████
      │                                                  ██████████
    4 │                                                            ██████
    2 │
      └─────────────────────────────────────────────────────────────────► Time
       3M      6M      9M      12M     15M     18M     21M (TAL Minted)
```

### Why Halving?

1. **Creates Scarcity**: Rewards decrease over time, making TAL more scarce
2. **Incentivizes Early Mining**: Higher rewards for early adopters
3. **Sustainable Emissions**: Prevents excessive inflation
4. **Predictable Supply**: Community knows exact emission schedule

## Token Utility

TAL has multiple utilities within the CrystalSupply ecosystem:

### 1. Staking Rewards

Stake TAL to earn auto-compounding protocol revenue:

```
Staking APR = (Protocol Fees + Buyback Revenue) / Total Staked TAL
```

**Revenue Sources:**
- 10% vault fee from all mining rounds
- Protocol-driven buybacks
- Future revenue streams (governance, etc.)

### 2. Governance (Coming Soon)

TAL holders will be able to vote on:
- Protocol parameter changes
- Fee structure adjustments
- Treasury allocation
- Feature proposals

### 3. Value Accrual

TAL accrues value through:
- **Mining Demand**: Users need TAL to profit from early mining
- **Staking Demand**: Holders stake for passive income
- **Buyback Pressure**: Protocol buys TAL with vault funds
- **Deflationary Mechanics**: Halving reduces emission

### 4. Liquidity Mining (Future)

Provide TAL liquidity on DEXs to earn:
- Trading fees
- Liquidity mining rewards
- Protocol incentives

## Fee Structure

The protocol generates revenue through fees on mining activities:

### Mining Fees (On Winning)

When your block wins, protocol takes **11% fee** from your staked MON:

| Fee Component | Percentage | Destination |
|---------------|------------|-------------|
| Vault Fee | 10% | Protocol vault (buybacks + staking) |
| Admin Fee | 1% | Development & operations |
| **Total** | **11%** | |

### Mining Fees (On Losing)

When your block loses, you pay a smaller **1.1% fee**:

| Fee Component | Percentage | Destination |
|---------------|------------|-------------|
| Vault Fee | 1% | Protocol vault |
| Admin Fee | 0.1% | Development |
| **Total** | **1.1%** | |

### Refining Fee (Optional)

When claiming refined TAL rewards early:
- **10% fee** on the refined amount
- Encourages patience and reduces sell pressure

### Keeper Fee

For automated checkpointing:
- **0.1 MON per checkpoint** (configurable)
- Paid to keeper operators
- Optional - you can claim manually

## Protocol Revenue Flow

```
Mining Rounds
     │
     ├─► 11% Winner Fee ──┐
     │                     │
     └─► 1.1% Loser Fee ───┤
                           │
                           ▼
                    Protocol Vault
                           │
                           ├─► Buyback TAL from market
                           │        │
                           │        └─► Burn or distribute to stakers
                           │
                           └─► Accumulate for staking rewards
```

## Deflationary Mechanisms

CrystalSupply has multiple deflationary forces:

### 1. Halving Emissions

Every 3M TAL minted, rewards halve:
- Reduces new TAL entering circulation
- Creates scarcity over time
- Predictable and transparent

### 2. Protocol Buybacks

10% of all mining fees goes to vault:
- Used to buy TAL from the market
- Creates buy pressure
- Can be burned or distributed to stakers

### 3. Staking Lock-up

When users stake TAL:
- Tokens are locked in staking contract
- Reduces circulating supply
- Creates long-term holding incentive

### 4. Opportunity Cost

Rational miners will stake their TAL:
- Auto-compounding returns attractive
- Reduces selling pressure
- Aligns incentives long-term

## Circulating Supply Dynamics

### Initial Phase (First 3M TAL)

```
Circulating Supply Growth (Era 0)

   32 TAL per round
   ~60 second rounds
   = ~1,920 TAL per hour
   = ~46,080 TAL per day

Expected time to first halving: ~65 days
```

### Mid-term (After Multiple Halvings)

As halvings occur:
- Emission rate decreases
- Buy pressure may increase
- Staking becomes more attractive
- TAL becomes more scarce

### Long-term (Final Halving Era)

Eventually:
- Only 0.5 TAL per round emitted
- Near max supply (21M)
- Protocol relies on fee revenue
- Stakers earn from mature protocol

## Comparison to Other Models

### vs. Bitcoin

| Feature | Bitcoin | CrystalSupply (TAL) |
|---------|---------|---------------------|
| Max Supply | 21M BTC | 21M TAL |
| Halving | Every 210k blocks (~4 years) | Every 3M TAL minted |
| Mining | Energy-intensive PoW | Stake-based, energy efficient |
| Fair Launch | ✅ Yes | ✅ Yes |
| Pre-mine | ❌ No | ❌ No |

### vs. ORE (Solana)

| Feature | ORE | CrystalSupply (TAL) |
|---------|-----|---------------------|
| Blockchain | Solana | Monad (EVM) |
| Max Supply | 5M ORE | 21M TAL |
| Halving | No | Yes (every 3M) |
| Staking | Manual rewards | Auto-compounding |
| Mining | Hash-based | Grid + VRF |

### vs. Traditional DeFi Tokens

| Feature | Typical DeFi | CrystalSupply (TAL) |
|---------|--------------|---------------------|
| Team Allocation | 15-30% | 0% |
| Investor Rounds | 20-40% | 0% |
| Pre-mine | Common | None |
| Emissions | Inflationary | Deflationary (halving) |
| Fair Launch | Rare | ✅ Yes |

## Economic Game Theory

### For Miners

**Early Game:**
- High rewards (32 TAL per round)
- Less competition
- Accumulate TAL cheaply

**Mid Game:**
- Halving kicks in
- Rewards decrease
- Mining becomes more competitive
- TAL price likely higher

**End Game:**
- Very low emissions (0.5 TAL/round)
- Mining competes with market buying
- Staking becomes primary TAL acquisition

### For Stakers

**Why Stake?**
- Auto-compounding returns
- Earn from protocol growth
- No lock-up period
- Better than holding idle TAL

**Incentive Alignment:**
- Miners → Stake to earn more
- Stakers → Long-term holders
- Protocol → Grows from both groups

### For Traders

**Buy Pressure:**
- Miners accumulating for staking
- Protocol buybacks (vault)
- Decreasing emissions (halving)

**Sell Pressure:**
- Miners selling rewards
- Stakers withdrawing (no lock)
- Market dynamics

## Token Burn Mechanism

While TAL token has a `burn()` function, the protocol currently does not implement automatic burns. However:

- **Buyback capability**: Vault can buy TAL from market
- **Future burns**: Governance may vote to burn bought TAL
- **Deflationary option**: Community decides burn policy

## Long-term Sustainability

### Phase 1: Bootstrap (0-3M TAL)
- High emissions attract miners
- Community grows
- Liquidity builds
- Protocol fees accumulate

### Phase 2: Growth (3M-12M TAL)
- Multiple halvings occur
- TAL price discovery
- Staking ecosystem matures
- Protocol revenue grows

### Phase 3: Maturity (12M-21M TAL)
- Low emissions
- Established TAL value
- Staking yields stabilize
- Protocol self-sustaining

### Post-Max Supply
- No new TAL mined (21M cap)
- Staking rewards from fees only
- Mature protocol economy
- TAL becomes pure value store

## Summary

Crystal (TAL) tokenomics are designed for:

✅ **Fairness**: 100% community mined, no pre-mine
✅ **Scarcity**: 21M max supply with halving
✅ **Utility**: Staking, governance, value accrual
✅ **Sustainability**: Fee-driven revenue model
✅ **Deflation**: Multiple deflationary mechanisms

This creates a sustainable, fair, and valuable ecosystem for all participants.

---

**Next Steps:**
- [Understand the Halving Mechanism](halving.md)
- [Learn About Fee Distribution](fees.md)
- [Start Mining TAL](../guides/mining.md)
- [Stake Your TAL](../guides/staking.md)
