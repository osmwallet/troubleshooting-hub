<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Activating an XRP Ledger account

An XRP Ledger account starts to exist when it is funded with at least the base reserve. Before that there is a key and an address but no account, which is why an unfunded wallet shows nothing and why a first withdrawal below the reserve cannot complete. Activation is the first payment, and it has to clear that minimum.

## What "activation" means

Creating a key is instant and free. Creating an account on the ledger is a transaction: someone must send XRP to the address, and the ledger creates the account entry as part of accepting that payment. The amount must cover the base reserve, because the new account is required to hold it.

That is why the wallet can show an address before the account exists. The address is derived from the key and is valid immediately; the ledger simply has no entry for it yet. Sending to it before activation is still the correct way to activate it.

## The first payment

1. **Copy the address** from the wallet's receive screen and confirm both ends of it.
2. **Send an amount above the base reserve**, not exactly at it, so the account has something spendable after activation.
3. **Wait for the payment to validate.** Activation happens with the transaction, not on a timer.
4. **Refresh or reopen the wallet** if the balance does not appear immediately; the account exists on the ledger whether or not the app has read it yet.
5. **Confirm the available amount** is what you expect once the reserve is subtracted.

Step two is where people save a fraction of an XRP and cost themselves an afternoon. Funding exactly at the reserve produces an account that exists and can send nothing.

## Why a small first withdrawal fails

Exchanges vary, but the pattern is the same: a withdrawal that cannot cover the destination account's reserve does not activate it, and some services refuse it outright. The wallet cannot fix this from its side, because the ledger's requirement is what the exchange is applying.

The practical rule is to make the first deposit comfortably above the reserve and treat the excess as spending money. The arithmetic, and why the balance and the available amount differ afterwards, is in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md).

## Activating an account you did not create

An address you were given may already be active, and sending to it simply funds it. Whether it is active is a ledger fact, not something a wallet can infer from the address. If you are unsure, a small test payment tells you: it either activates the account or adds to it.

That is also why a test payment is the standard first move for any new destination. It proves the address is valid, proves the payment path works, and in this specific case proves the account now exists.

## When activation goes wrong

Three failures look similar and have different causes.

| What you see | Likely cause | What to do |
|---|---|---|
| Payment sent, balance still zero | Account does not exist yet, or the amount was below the reserve | Check the transaction on the ledger; fund above the reserve |
| Account exists, nothing available | The deposit covered the reserve and no more | Send a small additional amount |
| Payment never arrives | Wrong address or wrong network | Do not resend; re-read the address from the wallet |
| Balance appears, then vanishes | Wallet is showing testnet | Switch back to mainnet |

The last row catches people who explored the testnet. It is a separate ledger and a separate account, covered in [Switching between testnet and mainnet](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-testnet-and-mainnet-switch.md).

## After the account exists

Two things become possible that were not before: the account can hold trustlines, and it can be closed again to recover the reserve. Both are deliberate operations with reserve consequences, described in *Issued tokens and TrustLines in practice* and *Deleting an account and recovering the reserve*.

It is also the moment to prove the backup. Activation funds a key you have written down; if that phrase is wrong, the account is now holding XRP that cannot be recovered. Reading it back carefully before the first deposit costs a minute and is the cheapest insurance in self-custody.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows the receive address for the selected account, reports the balance and the available amount the ledger returns, and keeps the reserve visible so an unfunded or reserve-only account is obvious rather than mysterious.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; an older build may display the account screen differently.

For the first-run order that avoids most of this, see [First run: the setup checklist](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-first-run-setup-checklist.md). For the full-balance case where activation is not the issue, *Sending your full XRP balance*, and for a withdrawal path with its own rules, *Moving XRP from an exchange into your own wallet*.

### FAQ

### How much XRP activates an account?

At least the base reserve, and more if you want the account to be able to send anything afterwards. Fund above the minimum rather than at it.

### Can I activate an account by receiving an issued token?

No. Tokens require a trustline, and a trustline cannot exist on an account that does not exist. XRP has to fund the account first.

### Does activation cost extra?

No, the reserve is held rather than spent. You are moving XRP into an account, not paying a fee to create one, and the reserve returns if the account is closed later.

### Why does the exchange say the address is invalid?

Some withdrawal forms validate addresses against accounts they can see, and an unfunded address is not visible as an account yet. Use a service that permits sending to a new address, or fund the account from a wallet you already hold.
