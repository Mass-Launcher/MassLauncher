# How MassLauncher works

A deeper technical look at how MassLauncher mass-launches meme coins on pump.fun.

## The 30-second pitch

MassLauncher is a hosted service. You sign in (Telegram, Google, or email), deposit SOL to a wallet we generate for your account, configure a memecoin (name, ticker, image, socials), and fire as many parallel launches on pump.fun as you want.

Every launch lands in pump.fun's new-pairs feed. Mass-launching floods that feed.

## Architecture (high-level)

```
┌─────────────────┐         ┌──────────────────┐         ┌──────────────┐
│   Web / TG bot  │ ──────▶ │  MassLauncher    │ ──────▶ │   pump.fun   │
│   (your input)  │         │  backend         │         │   (mints)    │
└─────────────────┘         └──────────────────┘         └──────────────┘
                                     │
                                     ▼
                            ┌──────────────────┐
                            │ Solana wallet    │
                            │ pool (pre-funded)│
                            └──────────────────┘
```

When you trigger a launch of N coins:

1. **Wallet pool checkout** — N pre-funded wallets are reserved from a shared pool. Each already holds enough SOL to cover rent + the pump.fun bonding-curve seed.
2. **Metadata upload** — Coin image + JSON metadata is pushed to pump.fun's IPFS in parallel.
3. **Transaction crafting** — N pump.fun create-coin transactions are built and signed.
4. **Parallel submission** — All transactions go out to Solana RPC at once. They typically land within a single Solana slot of each other (~400ms apart on-chain).
5. **Confirmation batch** — Signature statuses polled in a single batch RPC call.
6. **Pool checkin** — Used wallets are returned to the pool for future launches.

## Why pre-funded wallets?

Each pump.fun create-coin transaction needs the launching wallet to hold a small amount of SOL (rent + initial buy). If we funded a fresh wallet for every launch, you'd wait 12-15 seconds for the funding transaction to confirm before the actual launch could fire.

By keeping a pool of pre-funded wallets, **launch latency drops to one Solana slot** — the time it takes for a single transaction to land.

## Why parallel?

Sending N transactions in parallel (rather than sequentially) means the wall-clock time for 25 launches is roughly the same as for 1 launch. We've benchmarked 100-coin mass launches completing in under 15 seconds wall-clock.

## Pricing logic

The per-launch price slides linearly:

```
price(n) = max(0.015, 0.02 - 0.00005 * (n - 10))   # SOL per launch
```

- Launches 1–10: flat 0.02 SOL
- Launch 11: 0.01995 SOL
- Launch 50: ~0.0175 SOL
- Launch 100+: 0.015 SOL (floor)

This is computed per-account, so heavy users always pay the floor rate.

## Why use a hosted service vs. running your own?

You could write a Solana script and fire pump.fun create-coin instructions yourself. Most people don't because:

- **Rent + funding overhead** — every fresh wallet needs ~0.012 SOL bootstrapped first.
- **RPC selection + retry logic** — picking the right RPC, handling timeouts, batching confirmations.
- **Metadata upload** — pump.fun expects metadata in a specific shape on IPFS.
- **Wallet sweeping** — after launches finish, residual SOL needs to be reclaimed.

MassLauncher handles all of that. You pay a flat per-launch fee and get the speed of a tuned wallet pool.

---

📖 More docs:

- [`pricing.md`](pricing.md) — detailed pricing breakdown
- [`faq.md`](faq.md) — common questions

🌐 Try it: **[masslauncher.fun](https://masslauncher.fun)**
