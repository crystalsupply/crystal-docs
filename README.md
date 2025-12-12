# CrystalSupply Documentation

Welcome to the official documentation for CrystalSupply - a fair, decentralized mining protocol on Monad blockchain.

## What is CrystalSupply?

CrystalSupply is an EVM-based mining protocol that reimagines crypto mining for the modern blockchain era. Built on Monad, it combines:

- **Fair Mining**: Round-based mining system with provable randomness via Pyth Entropy
- **Auto-Compounding Staking**: Earn passive rewards that automatically compound
- **Deflationary Tokenomics**: Halving mechanism every 3M TAL minted
- **Community-Driven**: Transparent, on-chain mechanics with no pre-mine

## Key Features

### 🎯 Grid-Based Mining
Mine TAL by staking MON on a 25-block grid. Each round, one block is randomly selected as the winner using Pyth's Entropy VRF.

### 💎 Crystal (TAL) Token
- **Max Supply**: 21,000,000 TAL
- **Halving**: Rewards halve every 3M TAL minted
- **Initial Reward**: 32 TAL per round
- **Decimals**: 18

### 📈 Auto-Compounding Staking
Stake your TAL tokens to earn auto-compounding rewards from protocol fees and buybacks. No manual claiming needed - your balance grows automatically!

### 🔐 Provably Fair
All randomness is generated using Pyth Entropy V2, ensuring transparent and verifiable outcomes for every mining round.

## Quick Links

- [**Getting Started**](getting-started/introduction.md) - New to CrystalSupply? Start here!
- [**Mining Guide**](guides/mining.md) - Learn how to mine TAL
- [**Staking Guide**](guides/staking.md) - Stake TAL and earn rewards
- [**Tokenomics**](fundamentals/tokenomics.md) - Understand TAL economics
- [**Smart Contracts**](technical/contracts.md) - Technical documentation

## Community

- **Website**: [Coming Soon]
- **Twitter**: [Coming Soon]
- **Discord**: [Coming Soon]
- **GitHub**: [Coming Soon]

## Architecture Overview

```
┌─────────────────────────────────────────────┐
│           CrystalSupply Protocol            │
├─────────────────────────────────────────────┤
│                                             │
│  ┌──────────────┐      ┌─────────────────┐ │
│  │   Crystal    │◄─────┤ CrystalSupply   │ │
│  │   (TAL)      │      │  (Mining)       │ │
│  │   Token      │      │                 │ │
│  └──────┬───────┘      └────────┬────────┘ │
│         │                       │          │
│         │                       │          │
│         ▼                       ▼          │
│  ┌──────────────┐      ┌─────────────────┐ │
│  │  Staking     │      │  Pyth Entropy   │ │
│  │  (Auto-Comp) │      │  (VRF)          │ │
│  └──────────────┘      └─────────────────┘ │
│                                             │
└─────────────────────────────────────────────┘
```

## Why CrystalSupply?

Unlike traditional mining that requires expensive hardware, CrystalSupply democratizes mining through:

1. **Accessibility**: Mine with just a wallet and MON tokens
2. **Transparency**: All operations on-chain, fully auditable
3. **Sustainability**: No energy-intensive proof-of-work
4. **Community First**: Fair launch with no pre-mine or team allocation
5. **Auto-Compounding**: Staking rewards automatically reinvest

Ready to start? Head to the [Getting Started](getting-started/introduction.md) guide!
