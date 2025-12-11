# Wallet Setup

Learn how to configure your Web3 wallet to work with CrystalSupply on the Monad blockchain.

## Supported Wallets

CrystalSupply works with any Web3 wallet that supports EVM-compatible chains:

### Desktop Wallets
- ✅ **MetaMask** - Most popular, great for beginners
- ✅ **Rabby** - Advanced features, multi-chain support
- ✅ **Coinbase Wallet** - Easy to use, integrated exchange
- ✅ **Rainbow** - Beautiful UI, mobile + desktop

### Mobile Wallets
- ✅ **MetaMask Mobile** - Full mobile version
- ✅ **Trust Wallet** - Popular mobile wallet
- ✅ **Coinbase Wallet** - Mobile app available
- ✅ **imToken** - Secure mobile wallet

### Hardware Wallets
- ✅ **Ledger** - Industry standard, works with MetaMask
- ✅ **Trezor** - Secure, works with MetaMask
- ✅ **GridPlus Lattice** - Advanced security

## Setting Up MetaMask

MetaMask is the most popular choice. Here's how to set it up:

### Step 1: Install MetaMask

**Desktop (Chrome/Firefox/Brave):**
1. Go to [metamask.io](https://metamask.io)
2. Click "Download"
3. Select your browser
4. Install the extension
5. Create new wallet or import existing

**Mobile (iOS/Android):**
1. Download "MetaMask" from App Store or Google Play
2. Open app and create/import wallet
3. Secure your seed phrase (NEVER share it!)

### Step 2: Add Monad Network

Once MetaMask is installed:

**Method 1: Automatic (Recommended)**
1. Visit CrystalSupply app
2. Click "Connect Wallet"
3. Approve "Add Network" request
4. Monad network added automatically!

**Method 2: Manual Configuration**

1. Open MetaMask
2. Click network dropdown (top)
3. Click "Add Network" or "Add Network Manually"
4. Enter Monad details:

```
Network Name: Monad
RPC URL: [Monad RPC URL - TBD]
Chain ID: [Monad Chain ID - TBD]
Currency Symbol: MON
Block Explorer URL: [Monad Explorer - TBD]
```

5. Click "Save"
6. Switch to Monad network

### Step 3: Get MON Tokens

You need MON for:
- Mining stakes (minimum 0.1 MON per block)
- Gas fees for transactions

**How to Get MON:**

Option 1: Bridge from Ethereum
```
1. Go to [Monad Bridge - TBD]
2. Connect your wallet
3. Select amount to bridge
4. Confirm transaction
5. Wait for bridge (~5-15 minutes)
```

Option 2: Buy on Exchange
```
1. Buy MON on [Exchange Name - TBD]
2. Withdraw to your wallet address
3. Select Monad network
4. Confirm withdrawal
```

Option 3: Swap on Monad DEX
```
1. Go to [Monad DEX - TBD]
2. Swap other tokens for MON
3. Confirm transaction
```

### Step 4: Connect to CrystalSupply

1. Go to [CrystalSupply App URL - TBD]
2. Click "Connect Wallet"
3. Select MetaMask
4. Approve connection in popup
5. You're connected! ✅

You should now see:
- Your MON balance
- Your TAL balance (if any)
- Mining interface

## Security Best Practices

### Seed Phrase Security

Your seed phrase is the master key to your wallet. **Protect it!**

✅ **DO:**
- Write it down on paper
- Store in multiple secure locations
- Use a metal backup (fire/water resistant)
- Memorize it if possible

❌ **DON'T:**
- Share it with anyone (not even support!)
- Store it digitally (no screenshots, cloud storage, etc.)
- Send it via email, chat, or text
- Enter it on websites (only in wallet app)

### Transaction Safety

Before confirming any transaction:

1. ✅ **Check the contract address** - Verify it matches official addresses
2. ✅ **Review the amount** - Make sure MON/TAL amounts are correct
3. ✅ **Verify permissions** - Only approve what's necessary
4. ✅ **Check gas fees** - Ensure fees are reasonable

### Phishing Protection

**Warning Signs of Phishing:**
- ❌ Unexpected DMs asking for seed phrase
- ❌ "Support" asking you to "validate" wallet
- ❌ Websites with typos in URL
- ❌ Too-good-to-be-true offers
- ❌ Urgent requests to act immediately

**How to Stay Safe:**
- ✅ Bookmark official CrystalSupply URL
- ✅ Verify URLs before entering
- ✅ Only download wallets from official sites
- ✅ Enable MetaMask phishing protection
- ✅ Use hardware wallet for large amounts

### Permission Management

Regularly review and revoke unnecessary approvals:

**Check Approvals:**
1. Go to [Monad Explorer - TBD]
2. Enter your wallet address
3. View "Token Approvals"
4. Revoke any suspicious or old approvals

Or use tools like:
- [Revoke.cash](https://revoke.cash) (if supported)
- [Approved.zone](https://approved.zone)

### Multi-Signature for Large Amounts

For significant TAL holdings, consider:
- **Gnosis Safe** - Multi-sig wallet on Monad
- **Hardware wallet** - Ledger or Trezor
- **Multiple wallets** - Split funds across addresses

## Common Issues & Solutions

### "Wrong Network" Error

**Problem:** MetaMask is on different network

**Solution:**
1. Open MetaMask
2. Click network dropdown
3. Select "Monad"

### "Insufficient Funds" Error

**Problem:** Not enough MON for gas or stake

**Solution:**
1. Check your MON balance
2. Get more MON (bridge, buy, or swap)
3. Try again

### "Transaction Failed"

**Problem:** Transaction reverted or failed

**Common Causes:**
- Gas too low → Increase gas limit
- Round ended → Try new round
- Below minimum → Stake at least 0.1 MON
- Slippage too low → Increase slippage tolerance

### Can't Connect Wallet

**Problem:** Wallet not connecting to app

**Solutions:**
1. Refresh the page
2. Disconnect and reconnect wallet
3. Clear browser cache
4. Try different browser
5. Update MetaMask to latest version

### Pending Transaction Stuck

**Problem:** Transaction pending for long time

**Solutions:**

**Option 1: Wait**
- Sometimes just takes a while
- Check gas price and network congestion

**Option 2: Speed Up**
1. Click pending transaction in MetaMask
2. Click "Speed Up"
3. Increase gas price
4. Confirm

**Option 3: Cancel**
1. Click pending transaction
2. Click "Cancel"
3. Confirm cancellation transaction

### Lost Seed Phrase

**Problem:** Can't find your seed phrase

**Solution:**
- If wallet still open: Export seed phrase from settings
- If wallet locked and phrase lost: **Funds are unrecoverable**
- **Prevention:** Store backup securely!

## Advanced Configuration

### Custom RPC for Better Performance

If default Monad RPC is slow, try:

**Alternative RPCs:**
```
Primary: [RPC 1 - TBD]
Backup: [RPC 2 - TBD]
Fast: [RPC 3 - TBD]
```

Add in MetaMask:
1. Settings → Networks → Monad
2. Change RPC URL
3. Save

### Hardware Wallet Setup

For maximum security, use Ledger/Trezor:

**Ledger:**
1. Connect Ledger to computer
2. Open Ethereum app on Ledger
3. In MetaMask: Connect Hardware Wallet
4. Select Ledger
5. Choose account
6. Connect

**Trezor:**
1. Connect Trezor to computer
2. Unlock Trezor
3. In MetaMask: Connect Hardware Wallet
4. Select Trezor
5. Choose account
6. Connect

**Note:** Monad transactions work same as Ethereum!

### Multiple Accounts

Manage multiple wallets in MetaMask:

**Create New Account:**
1. Click account icon (top right)
2. "Create Account"
3. Name it (e.g., "Mining Account", "Staking Account")
4. Confirm

**Import Existing Account:**
1. Click account icon
2. "Import Account"
3. Enter private key or seed phrase
4. Confirm

**Use Case:**
- Account 1: Active mining
- Account 2: Long-term staking
- Account 3: Trading/liquidity

## Mobile Setup

### MetaMask Mobile

**Setup:**
1. Download MetaMask from app store
2. Create or import wallet
3. Tap hamburger menu (☰)
4. Settings → Networks → Add Network
5. Enter Monad details
6. Save

**Connect to CrystalSupply:**
1. Open MetaMask browser (in app)
2. Navigate to CrystalSupply URL
3. Connect wallet
4. Start mining from mobile!

**Tips for Mobile:**
- Use WiFi for better connection
- Keep app updated
- Enable biometric unlock
- Backup seed phrase securely

### Trust Wallet

**Setup:**
1. Download Trust Wallet
2. Create/import wallet
3. Tap Settings → Network
4. Add Custom Network
5. Enter Monad details
6. Save

**Connect:**
- Use WalletConnect to connect to CrystalSupply
- Scan QR code or paste link
- Approve connection

## Wallet Comparison

| Feature | MetaMask | Rabby | Coinbase | Hardware |
|---------|----------|-------|----------|----------|
| **Ease of Use** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Security** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Mobile** | ✅ Yes | ❌ No | ✅ Yes | ⚠️ Limited |
| **Multi-Chain** | ✅ Yes | ✅ Yes | ✅ Yes | ✅ Yes |
| **Cost** | 🆓 Free | 🆓 Free | 🆓 Free | 💰 $50-200 |
| **Best For** | Beginners | Power users | Easy onramp | Large holdings |

## Next Steps

Wallet setup complete? Now you can:

1. [Get your first MON tokens](#step-3-get-mon-tokens)
2. [Start mining TAL](quick-start.md)
3. [Learn mining strategies](../guides/strategy.md)
4. [Stake your TAL](../guides/staking.md)

## Need Help?

- **MetaMask Support:** [support.metamask.io](https://support.metamask.io)
- **CrystalSupply Discord:** [Discord Link - TBD]
- **Community Forum:** [Forum Link - TBD]
- **FAQ:** [Read FAQ](../guides/faq.md)

Stay safe and happy mining! 💎⛏️
