# MassLauncher FAQ

Common questions about mass launching meme coins on pump.fun.

## General

### What is mass launching on pump.fun?

Mass launching means firing many meme coin launches on pump.fun in rapid succession. Every launch lands in pump.fun's new-pairs feed. Spam-launching 25, 50, or 100 coins floods that feed with your tokens — getting free organic visibility without any ad spend.

### What's the point?

Three main use cases:

1. **Project promotion** — Flood new-pairs with launches that all reference your main token's CA or socials. Eyes land on your project for free.
2. **Reviving a dead coin** — Spam launches that point back to an existing coin. The chart often notices.
3. **Volume / liquidity probing** — Hundreds of micro-launches generate on-chain activity around your project.

### Is mass launching legal?

It's pump.fun usage. Whether spam-launching is allowed depends on pump.fun's terms of service, which can change. MassLauncher itself doesn't violate any Solana protocol rules. Use responsibly.

## Pricing

### How much does each pump.fun launch cost?

0.02 SOL each for the first 10 launches, then sliding linearly down to 0.015 SOL at 100 launches. After 100, you stay at the floor rate.

### Are there any hidden fees?

No. The per-launch fee covers everything: wallet funding, RPC fees, priority fees, pump.fun creation, metadata upload, confirmation polling.

### Can I get a refund if a launch fails?

Yes — failed launches are automatically refunded as credits. No ticket needed.

### Do credits expire?

No. Your credits stay on the account forever.

## Sign-in & account

### Do I need a Solana wallet to sign up?

No. MassLauncher creates a deposit wallet for your account on first sign-in. You can sign in with Telegram, Google, or email + password.

### Can I link a Solana wallet later?

Yes. The Account page lets you link a Solana wallet for asset withdrawals — it's optional.

### Can I use the same account on web and Telegram?

Yes. The web app and the [@MassLauncherBot](https://t.me/MassLauncherBot) Telegram bot share the same database. One account, two interfaces, one balance.

## Launches

### How fast is each launch?

Individual launches confirm on pump.fun in under 10 seconds.

### How fast is a mass launch of 25 coins?

Mass launches go out in parallel via the pre-funded wallet pool. 25 coins are typically minted within a **single Solana slot** of each other (~400ms apart on-chain). Wall-clock time is roughly the same as a single launch.

### Is there a launch limit?

Soft cap of 200 launches per day per account, to protect the shared wallet pool. Contact support if you need a higher cap.

### What if pump.fun changes their API?

MassLauncher tracks pump.fun's program updates. We push fixes within hours of any breaking change.

## Technical

### What RPC do you use?

We use Helius for confirmed-level reads and submission. Priority fees are tuned per-launch based on current network conditions.

### Where does the metadata get stored?

Coin metadata (name, ticker, image, description, socials) goes to pump.fun's IPFS gateway — same place every pump.fun coin's metadata lives.

### Can I see the source code?

No — MassLauncher is closed-source SaaS. This repository contains documentation only.

## Other

### How do I report a bug or security issue?

- Bug: open an issue on this repo
- Security: see [`SECURITY.md`](../SECURITY.md) for private channels

### Where can I follow updates?

- Twitter: [@masslauncher](https://x.com/masslauncher)
- Telegram: [@MassLauncherBot](https://t.me/MassLauncherBot) — `/changelog` for recent updates

---

🌐 Start mass launching: **[masslauncher.fun](https://masslauncher.fun)**
