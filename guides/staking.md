# Staking Guide

Learn how to stake your Crystal (TAL) tokens to earn auto-compounding rewards from protocol revenue!

## What is Staking?

Staking allows you to lock your TAL tokens in the staking contract to earn a share of protocol fees and buyback revenue. Unlike traditional staking, **CrystalSupply staking is fully auto-compounding** - your balance grows automatically without needing to claim!

## Key Features

### 🔄 Auto-Compounding

Your staked TAL automatically earns rewards that compound over time:

```
Your Balance = Your Shares × (Total Pooled TAL / Total Shares)
```

As rewards are distributed, `Total Pooled TAL` increases, making your shares more valuable!

### 🔓 No Lock-Up Period

- Withdraw anytime
- No minimum staking duration
- No withdrawal penalties
- Full flexibility

### 💰 Multiple Revenue Streams

Earn from:
1. **Mining Fees** - 10% vault fee from all mining rounds
2. **Protocol Buybacks** - TAL bought from market and distributed
3. **Future Revenue** - Additional streams as protocol grows

### 📊 Transparent Returns

- View your balance in real-time
- See total rewards distributed
- Track your lifetime earnings
- Fully on-chain and auditable

## How Auto-Compounding Works

CrystalSupply uses a **shares-based model** similar to Lido's stETH:

### The Math

When you deposit TAL:

```
Shares Minted = (Your Deposit × Total Shares) / Total Pooled TAL
```

When rewards are distributed:

```
Total Pooled TAL increases
→ Each share becomes worth more TAL
→ Your balance increases automatically!
```

### Example Walkthrough

**Initial State:**
- Total Pooled TAL: 100,000
- Total Shares: 100,000
- 1 share = 1 TAL

**You Deposit 1,000 TAL:**
- Shares minted: (1,000 × 100,000) / 100,000 = 1,000 shares
- New totals: 101,000 TAL, 101,000 shares
- Still 1 share = 1 TAL

**Protocol Distributes 10,000 TAL Rewards:**
- Total Pooled TAL: 101,000 + 10,000 = 111,000
- Total Shares: Still 101,000
- Now 1 share = 1.099 TAL!

**Your Balance Now:**
- Your shares: 1,000
- Your TAL: 1,000 × 1.099 = 1,099 TAL
- You earned 99 TAL automatically! 🎉

### Why Shares?

The shares model provides:
- **Gas Efficient**: No need to track per-user rewards
- **Automatic**: Balance updates without claiming
- **Fair**: Rewards proportional to stake and time
- **Scalable**: Works for any number of users

## Getting Started

### Step 1: Ensure You Have TAL

You need TAL tokens to stake. If you don't have any:
- [Mine TAL](mining.md)
- Buy TAL on DEXs
- Provide liquidity to earn TAL

### Step 2: Navigate to Staking

1. Go to CrystalSupply app
2. Click on "Staking" tab
3. Connect your wallet
4. View current staking statistics

### Step 3: Deposit TAL

1. **Enter Amount**: How much TAL to stake
2. **Preview**: See shares you'll receive
3. **Approve**: Allow staking contract to use your TAL
4. **Deposit**: Confirm transaction
5. **Done**: You're now earning!

```
Example Transaction:

Depositing: 1,000 TAL
Shares Minted: 950 shares
New Balance: 1,000 TAL

[Approve TAL] → [Deposit]
```

### Step 4: Watch Your Balance Grow

Your staked balance automatically increases as:
- Mining rounds generate fees
- Protocol executes buybacks
- Other revenue is distributed

**No claiming needed!** Just watch your balance in the staking dashboard.

## Withdrawing TAL

Need your TAL back? Withdraw anytime!

### How to Withdraw

1. **Navigate to Staking**
2. **Enter Amount**: How much TAL to withdraw (or leave 0 for all)
3. **Preview**: See shares that will be burned
4. **Withdraw**: Confirm transaction
5. **Receive TAL**: Tokens sent to your wallet

```
Example Withdrawal:

Withdrawing: 500 TAL
Shares Burned: 450 shares
TAL Received: 500 TAL (includes all rewards!)

[Withdraw]
```

### What You Get

When you withdraw, you receive:
- **Original Stake**: Your initial deposit
- **All Rewards**: Every reward earned since deposit
- **No Fees**: No withdrawal penalty

### Partial vs. Full Withdrawal

**Partial Withdrawal:**
- Specify exact amount to withdraw
- Remaining TAL stays staked
- Keeps earning rewards

**Full Withdrawal (Amount = 0):**
- Withdraws entire balance
- Burns all your shares
- Stops earning rewards

## Staking Metrics

Monitor these key metrics in the staking dashboard:

### Your Personal Stats

| Metric | Description |
|--------|-------------|
| **Staked Balance** | Your current TAL balance (auto-updating) |
| **Shares Owned** | How many shares you hold |
| **Initial Deposits** | Total TAL you've deposited |
| **Lifetime Rewards** | Total rewards earned all-time |
| **Current APR** | Estimated annual percentage rate |

### Global Stats

| Metric | Description |
|--------|-------------|
| **Total Pooled TAL** | All TAL in staking contract |
| **Total Shares** | All shares issued |
| **Total Rewards Distributed** | Lifetime rewards paid out |
| **Share Price** | Current TAL per share |

### Calculating Your Rewards

```
Your Current Balance = Your Shares × (Total Pooled / Total Shares)

Your Lifetime Rewards = Current Balance - Initial Deposits
```

Example:
- Your shares: 1,000
- Total pooled: 2,000,000 TAL
- Total shares: 1,800,000
- Share price: 2,000,000 / 1,800,000 = 1.111

```
Your Balance = 1,000 × 1.111 = 1,111 TAL

If you deposited 1,000 TAL initially:
Lifetime Rewards = 1,111 - 1,000 = 111 TAL earned
```

## Revenue Sources

Your staking rewards come from multiple sources:

### 1. Mining Fees (Primary)

Every mining round generates fees:

**Winner Fees:**
- 11% fee on winning stakes
- 10% goes to vault → staking rewards
- 1% goes to admin

**Loser Fees:**
- 1.1% fee on losing stakes
- 1% goes to vault → staking rewards
- 0.1% goes to admin

**Example:**
```
Round 500:
- Total winning stakes: 1,000 MON
- Winners pay: 110 MON fee (11%)
- To vault: 100 MON

- Total losing stakes: 5,000 MON
- Losers pay: 55 MON fee (1.1%)
- To vault: 50 MON

Total to vault: 150 MON this round
```

This MON accumulates in the vault and is used for:
- Buying TAL from the market
- Distributing to stakers

### 2. Protocol Buybacks

The vault periodically buys TAL:

```
Vault MON Balance
    ↓
Buy TAL from DEX
    ↓
Distribute to Stakers (increase Total Pooled TAL)
```

This creates:
- Buy pressure on TAL
- Rewards for stakers
- Sustainable value accrual

### 3. Future Revenue Streams

As the protocol grows, additional revenue may include:
- Governance fees
- Partnership revenue
- Additional protocol features

## APR Calculation

### Estimated APR Formula

```
APR = (Annual Rewards / Total Staked TAL) × 100%

Where:
Annual Rewards = (Recent Rewards / Time Period) × 365 days
```

### Factors Affecting APR

APR is dynamic and depends on:

📈 **Increases APR:**
- More mining activity (more fees)
- Higher TAL buybacks
- Fewer total stakers (less dilution)

📉 **Decreases APR:**
- Less mining activity
- More total stakers (more dilution)
- Lower protocol revenue

### Example APR Scenarios

**High Activity Scenario:**
- 100,000 TAL staked
- 10,000 TAL rewards per month
- APR = (10,000 × 12) / 100,000 = 120% APR

**Low Activity Scenario:**
- 500,000 TAL staked
- 5,000 TAL rewards per month
- APR = (5,000 × 12) / 500,000 = 12% APR

**Actual APR will vary based on real-time conditions!**

## Staking Strategies

### 1. Long-Term Hold Strategy

**Who:** Believers in long-term protocol growth

**Approach:**
- Stake all mined TAL immediately
- Never withdraw
- Maximize compounding effect

**Pros:**
- Maximum compound returns
- Simplest strategy
- Aligns with protocol growth

**Cons:**
- No liquidity
- Opportunity cost if TAL price moons

### 2. Partial Staking Strategy

**Who:** Balanced risk/reward preference

**Approach:**
- Stake 50-80% of TAL
- Keep rest liquid for trading
- Rebalance periodically

**Pros:**
- Earn rewards while staying liquid
- Flexibility to sell if needed
- Balanced approach

**Cons:**
- Miss out on some compounding
- More complex to manage

### 3. Yield Farming Strategy

**Who:** DeFi power users

**Approach:**
- Split TAL between staking and LP
- Provide liquidity on DEXs
- Earn trading fees + staking rewards

**Pros:**
- Multiple income streams
- Support protocol liquidity
- Potentially higher returns

**Cons:**
- Impermanent loss risk
- More complex
- Higher gas costs

### 4. Market Timing Strategy

**Who:** Active traders

**Approach:**
- Stake when expecting low TAL price
- Withdraw when expecting pumps
- Time the market

**Pros:**
- Maximize profits if correct
- Take advantage of volatility

**Cons:**
- Requires market knowledge
- Timing is difficult
- Higher gas fees from transactions

## Risks & Considerations

### Smart Contract Risk

Like all DeFi:
- Smart contracts can have bugs
- Always DYOR (Do Your Own Research)
- Consider protocol audits
- Start with small amounts

**Mitigations:**
- Protocol will be audited
- Open source code for review
- Community bug bounties

### APR Volatility

Staking APR is not fixed:
- Changes based on mining activity
- Depends on total staked amount
- Varies with TAL price

**Strategy:**
- Don't assume fixed returns
- Monitor APR trends
- Diversify income sources

### Opportunity Cost

Staked TAL is illiquid during events:
- Can't sell during TAL price pumps
- Must withdraw first (takes gas + time)
- Withdrawal during low liquidity may affect price

**Strategy:**
- Only stake what you can afford to lock
- Keep some TAL liquid for trading
- Plan ahead for known events

### Dilution

As more users stake:
- Your share of rewards decreases
- APR may decline
- Competition for yields

**Strategy:**
- Stake early for better rates
- Understand APR is dynamic
- Focus on absolute returns, not just APR

## Advanced: Understanding Shares

### Share Price Over Time

As rewards are distributed, share price increases:

```
Share Price = Total Pooled TAL / Total Shares

Initially: 100,000 / 100,000 = 1.0 TAL per share

After rewards: 150,000 / 100,000 = 1.5 TAL per share
```

### Deposit Dilution

When you deposit, you get shares at current price:

**Early depositor (share price = 1.0):**
- Deposits 1,000 TAL
- Gets 1,000 shares

**Late depositor (share price = 1.5):**
- Deposits 1,500 TAL
- Gets 1,000 shares

Both have 1,000 shares, but late depositor paid more TAL. This is fair because early depositor took earlier risk!

### Withdrawal Calculation

When you withdraw:

```
TAL Received = Shares Burned × Current Share Price
```

You always get current market value of your shares!

## Comparing to Other Protocols

### vs. Traditional Staking (Lock-up)

| Feature | Traditional | CrystalSupply |
|---------|-------------|---------------|
| Lock-up | Yes (weeks/months) | No lock-up |
| Claiming | Manual | Automatic |
| Compounding | Manual | Auto-compounding |
| Flexibility | Low | High |

### vs. ORE Staking (Solana)

| Feature | ORE | CrystalSupply |
|---------|-----|---------------|
| Compounding | Manual claim | Auto-compounding |
| Rewards | Fixed schedule | Protocol revenue |
| Lock-up | No | No |
| Blockchain | Solana | Monad (EVM) |

### vs. Liquidity Providing

| Feature | LP Farming | TAL Staking |
|---------|------------|-------------|
| Impermanent Loss | Yes | No |
| Complexity | Higher | Lower |
| Returns | Variable | Variable |
| Risk | Medium-High | Medium |

## FAQ

### How often are rewards distributed?

Rewards are distributed continuously as:
- Mining rounds complete (every ~60 seconds)
- Vault executes buybacks
- Other revenue events occur

Your balance updates in real-time!

### Do I need to claim rewards?

**No!** Rewards auto-compound into your balance. Just withdraw when you want your TAL.

### What if I deposit more TAL later?

You can deposit multiple times:
- New shares minted at current price
- Added to your existing shares
- All shares earn together

### Can I transfer my shares?

No, shares are non-transferable. They represent your stake in the pool and are bound to your address.

### What happens if I'm the only staker?

You earn 100% of all rewards! Early stakers have significant advantage.

### Is there a minimum or maximum stake?

- **Minimum**: No minimum (but consider gas costs)
- **Maximum**: No maximum (stake as much as you want)

## Next Steps

Ready to start earning?

1. [Mine TAL](mining.md) or buy TAL
2. Visit staking dashboard
3. Deposit your TAL
4. Watch your balance grow!

**Additional Resources:**
- [Technical: Staking Contract](../technical/staking-contract.md)
- [Understanding Tokenomics](../fundamentals/tokenomics.md)
- [Fee Structure](../fundamentals/fees.md)

Happy staking! 💎📈
