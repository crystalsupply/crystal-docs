# Contract Addresses

Official CrystalSupply smart contract addresses deployed on Monad mainnet.

## Core Contracts

### Crystal Token (TAL)

The native ERC20 token of CrystalSupply.

**Address:** `0x126e7B338D242c9B9D03d6243b9f501d137d3F58`

**Contract:** Crystal.sol
**Type:** ERC20 Token
**Decimals:** 18
**Max Supply:** 21,000,000 TAL

**Block Explorer:**
[View on Monadscan](https://monadscan.com/address/0x126e7B338D242c9B9D03d6243b9f501d137d3F58#code)

---

### CrystalSupply (Mining Contract)

The mining protocol contract.

**Address:** `0x0C37B4c1e658ab0E812b66c3D9884963097176a2`

**Block Explorer:**
[View on Monad Explorer](https://monadscan.com/address/0x0C37B4c1e658ab0E812b66c3D9884963097176a2#code)

---

### CrystalStakingComp (Staking Contract)

Auto-compounding staking contract for TAL.

**Address:** `0xD33F0c3a9B4B675893Bf297827C60e793878494e`

**Contract:** CrystalStakingComp.sol
**Type:** Auto-Compounding Staking
**Model:** Shares-based (like Lido stETH)

**Block Explorer:**
[View on Monad Explorer](https://monadscan.com/address/0xD33F0c3a9B4B675893Bf297827C60e793878494e#code)

---

### CrystalBuyback (Buyback Contract)

Protocol buyback mechanism for TAL.

**Address:** `0xFfb3837D0B12ECf7d37E753BC7A8EF7687f1490a`

**Contract:** CrystalBuyback.sol
**Type:** Buyback & Distribution
**Purpose:** Buy TAL with vault MON, distribute to stakers

**Key Functions:**
- Buyback TAL from DEX
- Distribute to staking contract

**Block Explorer:**
[View on Monad Explorer](https://monadscan.com/address/0xFfb3837D0B12ECf7d37E753BC7A8EF7687f1490a#code)

---

## External Dependencies

### Pyth Entropy V2

**Purpose:** Verifiable Random Function (VRF) oracle

**Integration:** Used by CrystalSupply for fair randomness

**Documentation:** [Pyth Entropy Docs](https://docs.pyth.network/entropy)

---