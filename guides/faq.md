# Frequently Asked Questions (FAQ)

Common questions about CrystalSupply, TAL token, mining, and staking.

## General Questions

### What is CrystalSupply?

CrystalSupply is a decentralized mining protocol on Monad blockchain that allows users to mine Crystal (TAL) tokens through a fair, grid-based system powered by verifiable randomness.

### What blockchain is CrystalSupply on?

CrystalSupply is built on **Monad**, a high-performance EVM-compatible blockchain with 10,000+ TPS and sub-second finality.

### Is there a pre-mine or team allocation?

**No!** 100% of TAL supply must be mined by the community. There is:
- ❌ No pre-mine
- ❌ No team allocation
- ❌ No investor rounds
- ✅ Pure fair launch

The only exception is 105,000 TAL initial circulating supply used for bootstrapping liquidity.

### How is CrystalSupply different from ORE?

| Feature | ORE (Solana) | CrystalSupply (Monad) |
|---------|--------------|----------------------|
| Blockchain | Solana | Monad (EVM) |
| Max Supply | 5M | 21M |
| Mining | Hash-based | Grid + VRF |
| Halving | No | Yes (every 3M) |
| Staking | Manual rewards | Auto-compounding |

### Is CrystalSupply audited?

Audit is currently pending. Status will be updated in [Audit Reports](../resources/audits.md).

## Mining Questions

### How do I start mining?

1. Get MON tokens (Monad's native currency)
2. Connect wallet to CrystalSupply app
3. Select blocks on the 25-block grid
4. Stake MON on your chosen blocks
5. Wait for round to end
6. Claim rewards if you win!

Full guide: [Mining Guide](mining.md)

### What's the minimum MON needed to mine?

**Minimum stake: 0.1 MON per block**

You also need a small amount of MON for gas fees.

### How long do mining rounds last?

**~60 seconds per round** (configurable by governance)

Plus ~12 seconds intermission for randomness generation.

### What are my chances of winning?

Each block has a **1/25 (4%) chance** of being selected as the winner.

Your share of the reward depends on how much you staked relative to others on the winning block.

### What happens if I lose?

You get **98.9% of your MON back**! Only 1.1% is taken as fees:
- 1% goes to protocol vault (buybacks + staking)
- 0.1% goes to admin wallet

### Can I mine multiple blocks at once?

**Yes!** You can stake on as many blocks as you want in the same round. This spreads your risk across multiple blocks.

### How is the winning block determined?

The winning block is selected using **Pyth Entropy V2**, a decentralized verifiable random function (VRF). This ensures:
- ✅ Unpredictable
- ✅ Verifiable
- ✅ Cannot be manipulated
- ✅ Fully transparent

### What is "Winner Take All" mode?

Rarely (~1% of rounds), a round becomes "Winner Take All":
- **Only** winning block participants get TAL
- Losers get full MON refunds (minus small fee)
- Winners share larger TAL rewards
- Adds excitement and variance!

### What is "Motherlode"?

Very rarely (~0.1% of rounds), a "Motherlode" occurs:
- Massive bonus TAL rewards
- Jackpot-style event
- Extra incentive for winners

### How do I claim my rewards?

Two options:

**Manual Claiming:**
1. Go to "My Rewards" section
2. Click "Claim TAL" for tokens
3. Click "Claim MON" for MON refunds
4. Pay gas for each transaction

**Keeper Auto-Checkpoint:**
- Keepers automatically process your rewards
- Small fee (0.1 MON default)
- More convenient for active miners

Full guide: [Claiming Rewards](claiming.md)

### What are refined vs. unrefined TAL?

**Refined TAL:**
- Available immediately after checkpoint
- Can be claimed right away
- No fee after waiting period
- 10% fee if claimed early

**Unrefined TAL:**
- Accumulates in your miner account
- Refines over time automatically
- Becomes claimable refined TAL

### Can I mine on mobile?

Yes! If you have a mobile Web3 wallet (MetaMask Mobile, Trust Wallet, etc.) that supports Monad network, you can mine from your phone.

## Staking Questions

### How does auto-compounding staking work?

CrystalSupply uses a **shares-based model**:

1. When you deposit TAL, you receive shares
2. Protocol distributes rewards to the staking pool
3. Total pooled TAL increases
4. Each share becomes worth more TAL
5. Your balance grows automatically!

No claiming needed - rewards auto-compound!

Full guide: [Staking Guide](staking.md)

### Is there a lock-up period for staking?

**No!** You can withdraw your staked TAL anytime with no penalties.

### Where do staking rewards come from?

Staking rewards come from:
1. **Mining Fees** - 10% vault fee from all mining rounds
2. **Protocol Buybacks** - TAL bought from market with vault MON
3. **Future Revenue** - Additional streams as protocol grows

### What's the APR for staking?

APR is **dynamic** and depends on:
- Mining activity (more rounds = more fees)
- Total TAL staked (less staked = higher APR per user)
- Protocol buyback activity

Check the staking dashboard for current APR!

### Do I need to claim staking rewards?

**No!** Rewards automatically compound into your balance. Just withdraw when you want your TAL.

### Can I stake and mine at the same time?

**Yes!** You can:
- Mine TAL in mining rounds
- Stake your TAL to earn rewards
- Do both simultaneously

Many users mine to accumulate TAL, then stake it for passive income.

### Is there a minimum or maximum stake?

- **Minimum**: No minimum (but consider gas costs)
- **Maximum**: No maximum (stake as much as you want!)

## Tokenomics Questions

### What is the max supply of TAL?

**21,000,000 TAL** (21 million)

Inspired by Bitcoin's 21M cap!

### How does the halving work?

TAL rewards halve **every 3,000,000 TAL minted**:

| Era | Reward per Round | TAL Minted |
|-----|------------------|------------|
| 0 | 32 TAL | 3M |
| 1 | 16 TAL | 3M |
| 2 | 8 TAL | 3M |
| 3 | 4 TAL | 3M |
| 4 | 2 TAL | 3M |
| 5 | 1 TAL | 3M |
| 6 | 0.5 TAL | Until max |

Full details: [Halving Mechanism](../fundamentals/halving.md)

### When will the first halving occur?

After **3,000,000 TAL** is mined from the current halving era.

At ~60 second rounds with 32 TAL per round:
- ~1,920 TAL per hour
- ~46,080 TAL per day
- **~65 days to first halving**

(Actual time varies based on round duration and participation)

### Can TAL be burned?

Yes! The TAL token has a `burn()` function. Anyone can burn their own TAL.

The protocol may also implement buyback-and-burn mechanisms via governance.

### What are the fees?

**Mining Fees (Winners):**
- 11% fee on your winning stake
- 10% → Vault (buybacks + staking)
- 1% → Admin (development)

**Mining Fees (Losers):**
- 1.1% fee on your losing stake
- 1% → Vault
- 0.1% → Admin

**Refining Fee (Optional):**
- 10% fee if claiming refined TAL early
- 0% fee if you wait for refining period

**Keeper Fee (Optional):**
- 0.1 MON per checkpoint (configurable)
- Only if using keeper auto-checkpointing

Full details: [Fees & Revenue](../fundamentals/fees.md)

## Technical Questions

### What wallets are supported?

Any Web3 wallet that supports Monad (EVM):
- MetaMask
- Rabby
- Trust Wallet
- Coinbase Wallet
- Rainbow
- And more!

### How do I add Monad to my wallet?

```
Network Name: Monad
RPC URL: [TBD]
Chain ID: [TBD]
Currency Symbol: MON
Block Explorer: [TBD]
```

Full guide: [Wallet Setup](../getting-started/wallet-setup.md)

### Are the contracts open source?

**Yes!** All smart contracts are open source and will be available on GitHub.

**License:** MIT

### Can the contracts be upgraded?

**No.** CrystalSupply contracts are **immutable** (not upgradeable). This ensures:
- No admin backdoors
- Code cannot change after deployment
- Maximum decentralization and trust

### Where can I view transactions?

On the Monad block explorer:
- [Monad Explorer URL - TBD]

All transactions, events, and contract state are fully transparent!

### What programming language are contracts written in?

**Solidity ^0.8.19** with OpenZeppelin libraries for security.

### How is randomness generated?

Using **Pyth Entropy V2**, a decentralized VRF (Verifiable Random Function):
- Cryptographically secure
- Verifiable on-chain
- Cannot be manipulated
- Transparent results

Full details: [Pyth Entropy Integration](../technical/entropy.md)

## Strategy Questions

### What's the best mining strategy?

It depends on your goals:

**Conservative (Low Risk):**
- Stake small amounts on many blocks
- Diversify to smooth variance
- Get consistent results over time

**Aggressive (High Risk):**
- Stake large amounts on few blocks
- Win big or lose (but still get MON back!)
- Higher potential rewards

**Balanced:**
- Moderate stakes on several blocks
- Good risk/reward trade-off
- Recommended for most miners

Full strategies: [Understanding Grid Strategy](strategy.md)

### Should I stake my mined TAL?

**Generally, yes!** Staking provides:
- Auto-compounding protocol revenue
- Passive income on your TAL
- No lock-up period
- Better than letting TAL sit idle

Unless you're actively trading, staking is usually optimal.

### How should I split between mining and staking?

Common approaches:

**All-In Mining:**
- Keep all MON for mining
- Maximize TAL accumulation
- Stake TAL as you earn it

**Balanced:**
- Mine with 50% of capital
- Provide liquidity with TAL
- Stake remaining TAL

**Passive Income Focus:**
- Mine to accumulate initial TAL
- Stake everything for passive income
- Live off staking yields

Choose based on your goals and risk tolerance!

### When should I claim vs. use keepers?

**Manual Claiming:**
- ✅ Save keeper fee (0.1 MON)
- ✅ Full control over timing
- ❌ Must pay gas for each claim
- ❌ Time consuming if mining actively

**Keeper Auto-Checkpoint:**
- ✅ Automatic and convenient
- ✅ Batches multiple rounds
- ✅ Saves time
- ❌ Small keeper fee

**Recommendation:** If you mine frequently (multiple times per day), keepers save gas and time. If you mine occasionally, manual claiming is fine.

## Troubleshooting

### My transaction failed. What should I do?

Common reasons and solutions:

**"Round ended":**
- Round finished before your transaction processed
- Try again in the new round

**"Below minimum stake":**
- Must stake at least 0.1 MON per block
- Increase your stake amount

**"Insufficient funds":**
- Not enough MON in wallet
- Get more MON or reduce stake amount

**"Gas too low":**
- Increase gas price in wallet
- Try again with higher gas

### I can't see my rewards

Make sure you've:
1. ✅ Won a round (check round history)
2. ✅ Checkpointed the round (manual or keeper)
3. ✅ Waited for refined TAL to finish refining

If still missing, check the block explorer for your transactions.

### Keeper didn't checkpoint my rewards

Possible reasons:
- Not enough unclaimed rewards to justify gas cost
- Keeper service temporarily down
- You can always claim manually!

### How do I contact support?

- **Discord:** [TBD]
- **Twitter:** [TBD]
- **Telegram:** [TBD]
- **Email:** [TBD]

Join the community for fast help!

## Future Development

### Will there be governance?

**Yes!** TAL holders will eventually be able to vote on:
- Protocol parameter changes
- Fee adjustments
- Treasury allocation
- New features

Details coming soon!

### Are there plans for liquidity mining?

Likely! Providing TAL liquidity on DEXs may earn:
- Trading fees
- Liquidity mining rewards
- Protocol incentives

Stay tuned for announcements!

### Will CrystalSupply expand to other chains?

Currently focused on Monad. Future multi-chain expansion is possible based on community demand and governance votes.

### What's on the roadmap?

Upcoming features (tentative):
- [ ] Governance system
- [ ] Liquidity mining incentives
- [ ] Mobile app
- [ ] Advanced analytics dashboard
- [ ] Cross-chain bridging
- [ ] And more!

## Still Have Questions?

- Join our [Discord Community](../resources/community.md)
- Read the full [Documentation](../README.md)
- Check [Technical Docs](../technical/contracts.md)
- Follow us on [Twitter](../resources/community.md)

We're here to help! 💎
