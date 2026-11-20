<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Switching between testnet and mainnet

Testnet is a separate XRP Ledger used for experiments, with its own accounts and worthless XRP. Mainnet is the real one. The same address exists on both and holds different things on each, which is why switching networks makes a real balance seem to vanish and a test balance appear out of nowhere.

## Two ledgers, one address

An address is derived from a key, and the derivation does not depend on which network you point at. So the same phrase produces the same address on both. What differs is whether anything was ever sent to that address on that ledger.

That is the whole explanation for the confusion. A wallet showing zero after a network switch is not losing funds; it is reading a ledger where the account has nothing.

| | Testnet | Mainnet |
|---|---|---|
| XRP value | None | Real |
| Purpose | Development and testing | Actual holdings |
| Account on your address | Probably empty | Whatever you funded |
| Suitable for a backup you care about | No | Yes |

## Why testnet exists

Developers need to try things without risking funds: creating accounts, adding trustlines, testing a payment path, checking what a failure looks like. A ledger where mistakes cost nothing is genuinely useful for that. Each network sets its own reserve requirement and keeps its own history, so a figure from one does not describe the other.

It is not useful for someone learning the wallet, because the XRP is not real and the lessons do not transfer. A payment that works on testnet proves the software works; it proves nothing about a payment to a real recipient.

## Switching safely

1. **Finish what you are doing** on the current network before switching.
2. **Change the network in the wallet** and wait for it to reconnect.
3. **Check the address** has not changed, because it will not; if it has, you are in a different account.
4. **Read the balance** and expect the other ledger's figure.
5. **Switch back** when the test is done, rather than leaving it set and forgetting.

Step five is the one that causes support questions weeks later, when a wallet appears empty and the cause is a switch made once and never reversed.

## The "my balance disappeared" case

If the balance vanished and the available amount is zero, check the network before anything else. This is the fastest diagnosis in the whole wallet, and it costs one click.

If the network is correct and the balance is still zero, the causes are different: an unfunded account, a reserve-only account, or a stale read, all covered in [Why the wallet shows zero available XRP](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/why-osmwallet-shows-zero-available-xrp.md).

## Testnet is not a rehearsal for a real payment

A testnet payment to an address your recipient gave you will not arrive, because that address is on mainnet. Equally, XRP you obtained on testnet cannot be moved to mainnet, because it does not exist there.

The only way to be sure a payment will land is to send a small real one and check, which is the same advice as for any new destination.

## Trustlines and tokens on two ledgers

Trustlines are per-ledger objects. One created on testnet does not exist on mainnet, and a token held on testnet is a different asset from the one with the same code on mainnet, issued by a different account.

That matters if you have been experimenting: importing the account on mainnet will show the mainnet trustlines, which may be none. The article on that is [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md).

## Practising on testnet without confusing later

Make a separate account for testing rather than reusing the one you keep real funds in. A separate phrase means the test account is disposable, its reserve is irrelevant, and the two cannot be muddled when you are tired and looking at a balance you half recognise.

If you do reuse the account, the discipline is to switch back immediately after each session, before doing anything else. Most of the confusion in this article comes from a test network left selected, not from anything the wallet does wrong.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It offers both networks and shows which one is active, so a testnet session is visible rather than silent, and balances are read from the selected ledger rather than cached across a switch.

It is actively maintained, and the current release is downloaded from the GitHub releases page. The network you are on is part of any bug report worth writing, because half of the confusing ones are a switch.

For the account side, [Activating an XRP Ledger account](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/activate-an-xrp-ledger-account-osmwallet.md); for the reserve, *The XRP reserve, explained without the confusion*; for what a trustline is, *Issued tokens and TrustLines in practice*.

### FAQ

### Why does my balance show zero after switching networks?

Because the account on that ledger has nothing in it. The address is the same on both networks; the holdings are not.

### Is testnet XRP worth anything?

No. It exists to make mistakes free, and it cannot be moved to mainnet or sold.

### Does switching networks move my funds?

No. It changes which ledger the wallet reads. Nothing is transferred by a network switch.

### Can I use the same phrase on both networks?

Yes, and the address will be identical on both. Treat the testnet copy as disposable and the mainnet one as the real account.

### Why did my trustline disappear?

Trustlines exist per ledger. A trustline added on testnet is not present on mainnet, even for the same address.
