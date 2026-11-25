# MassLauncher questions

### Is a batch one token or several?

A batch creates separate tokens on Pump.fun. Two successful launches using the same name and ticker have two different mint addresses. To distribute a token you already own, transfer that token instead. [Batch launcher vs. multisender](https://masslauncher.fun/blog/solana-mass-launcher-pump-fun).

### Can I use the same balance on Telegram and the web?

Yes, when both are linked to the same MassLauncher account. For an existing Telegram balance, use the Telegram sign-in or linking flow on the web, rather than assuming a new email account will pick it up. Connecting a browser wallet is optional. [Open the web app](https://masslauncher.fun/) or [open the bot](https://t.me/MassLauncherBot).

### Can I send a different Pump.fun token to buy credits?

Only if the payment screen specifically offers that mint. If the token option is absent, use the SOL instructions. If it is present, match the full mint address before sending; two tokens can have the same name. [How payments are credited](pricing.md).

### My batch says “pending.” Should I submit again?

Not yet. Open History and check that row. Its credit stays reserved while MassLauncher is waiting for a definitive result. Retrying early can create an extra mint. If a row is confirmed, copy its full mint address. If it definitively fails, check the error and the returned credit before retrying. [How to verify a result](https://masslauncher.fun/blog/verify-pump-fun-launch-solscan).

### Why does the wallet on Pump.fun look different from mine?

MassLauncher uses its own launch wallets. That wallet is recorded as the creator and the service receives the associated creator fees. Your deposit address identifies a payment, not the creator of your mint. [Service terms](https://masslauncher.fun/terms).

### Will the coins appear on Axiom or bring traffic to my project?

A confirmed mint is verifiable on Solana. Feed inclusion, visitors, trading volume and price are separate outcomes; none is guaranteed. The [published launch study](https://masslauncher.fun/blog/pump-fun-launch-visibility) explains the difference.

### Where can I get help?

For a payment or launch question, open [the Telegram bot](https://t.me/MassLauncherBot) and use its support link. Include the public transaction signature or job reference if you have one. Never share a private key, seed phrase or API key. For vulnerability reports, use [the private reporting channels](../SECURITY.md).
