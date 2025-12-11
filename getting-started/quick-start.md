# Quick Start Guide

Get started with CrystalSupply mining in just a few minutes!

## Prerequisites

Before you begin, make sure you have:

- [ ] A Web3 wallet (MetaMask, Rabby, etc.)
- [ ] MON tokens for mining (minimum 0.1 MON per block)
- [ ] Small amount of MON for gas fees
- [ ] Your wallet connected to Monad network

## Step 1: Setup Your Wallet

If you haven't set up Monad in your wallet yet, follow our [Wallet Setup Guide](wallet-setup.md).

### Add Monad Network to MetaMask

1. Open MetaMask
2. Click on the network dropdown (top)
3. Click "Add Network"
4. Enter Monad network details:

```
Network Name: Monad
RPC URL: [Monad RPC - TBD]
Chain ID: [Monad Chain ID - TBD]
Currency Symbol: MON
Block Explorer: [Monad Explorer - TBD]
```

## Step 2: Get MON Tokens

You'll need MON tokens to:
- Stake on mining blocks (minimum 0.1 MON per block)
- Pay for transaction gas fees

### Where to Get MON

- Bridge from Ethereum/other chains
- Buy on Monad DEXs
- [Add specific instructions based on Monad ecosystem]

## Step 3: Connect to CrystalSupply

1. Visit [CrystalSupply App URL - TBD]
2. Click "Connect Wallet"
3. Approve the connection in your wallet
4. You should see your MON balance displayed

## Step 4: Your First Mining Round

### Understanding the Grid

The mining interface shows a **25-block grid** (5x5). Each block can be selected for mining.

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

### Place Your First Stake

1. **Select a Block**: Click on one or more blocks (0-24)
2. **Enter Amount**: Enter MON amount to stake (min 0.1 MON)
3. **Approve Transaction**: Confirm in your wallet
4. **Wait for Round End**: Rounds last ~60 seconds

### What Happens Next

- The round timer counts down
- When it reaches 0, an intermission period begins (~12 seconds)
- Pyth Entropy generates the random winning block
- Results are displayed on screen
- Winners can claim their TAL rewards!

## Step 5: Understanding Rewards

### If You Win

Your block was selected! You'll receive:

- **TAL Tokens**: Share of the current round reward
- **MON Refund**: Your staked MON back (minus protocol fees)

### Reward Distribution

- **11% Protocol Fee**: Taken from your staked MON
  - 10% goes to protocol vault (buybacks + staking rewards)
  - 1% goes to admin wallet (development)
- **Remaining 89%**: Returned to you

### If You Lose

Don't worry! You get:

- **Your MON Back**: Full stake returned (minus smaller fees)
- **Another Chance**: Join the next round immediately

### Fee Breakdown for Losers

When your block doesn't win:
- **1.1% Total Fee** from your stake
- **1% Vault Fee**: Protocol revenue
- **0.1% Admin Fee**: Development funds
- **98.9% Returned**: Back to you

## Step 6: Claim Your Rewards

### Manual Claiming

1. Go to "My Rewards" section
2. Click "Claim TAL" for token rewards
3. Click "Claim MON" for your stake refunds
4. Confirm transactions in your wallet

### Keeper Auto-Checkpointing

To save on gas, you can have keepers automatically checkpoint your rewards:

- Keepers batch-process claims across multiple rounds
- Small keeper fee (0.1 MON by default)
- Convenient for active miners

Learn more in the [Claiming Rewards Guide](../guides/claiming.md).

## Step 7: Stake Your TAL

Once you've mined some TAL, you can stake it to earn auto-compounding rewards!

1. Navigate to "Staking" tab
2. Enter amount of TAL to stake
3. Approve and confirm transaction
4. Watch your balance grow automatically!

**Staking Benefits:**
- Auto-compounding rewards
- Earn from protocol fees
- Earn from buyback revenue
- No lock-up period
- Withdraw anytime

Learn more in the [Staking Guide](../guides/staking.md).

## Pro Tips for Beginners

### 1. Start Small
Your first few rounds should be learning experiences. Stake the minimum (0.1 MON) to understand the mechanics.

### 2. Diversify Your Blocks
Don't put all your MON on one block. Spread across multiple blocks to increase your chances.

### 3. Watch the Grid
Before each round, check:
- Total MON staked on each block
- Number of participants per block
- Blocks with fewer participants may have less competition

### 4. Understand the Odds
Each block has an equal 1/25 (4%) chance of winning. Your share of the reward depends on how much you staked relative to others on the winning block.

### 5. Set Up Keeper Auto-Claim
If you're mining frequently, keepers save you gas fees and time.

### 6. Stake Your Earnings
Don't let your TAL sit idle! Stake it to earn auto-compounding protocol revenue.

## Common Beginner Mistakes

❌ **Staking everything on one block**
→ Diversify across multiple blocks

❌ **Not checking block totals**
→ Blocks with more staked have more competition

❌ **Forgetting about gas fees**
→ Keep extra MON for transactions

❌ **Not staking TAL rewards**
→ Stake to earn passive income

❌ **Panic after losing**
→ Remember: you get your MON back! Try again

## Next Steps

Now that you've completed your first mining round, you're ready to:

- [Learn Advanced Mining Strategies](../guides/strategy.md)
- [Understand Tokenomics](../fundamentals/tokenomics.md)
- [Explore the Halving Mechanism](../fundamentals/halving.md)
- [Deep Dive: How Mining Works](../fundamentals/mining.md)

## Need Help?

- Check the [FAQ](../guides/faq.md)
- Join our [Discord Community](../resources/community.md)
- Read the [Mining Guide](../guides/mining.md) for detailed strategies

Happy mining! 💎⛏️
