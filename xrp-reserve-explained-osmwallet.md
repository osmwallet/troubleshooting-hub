<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# The XRP reserve, explained without the confusion

The reserve is XRP that the XRP Ledger requires an account to hold in order to exist. It is not a fee, it is not a wallet charge, and it does not go to anyone. It is the reason a wallet can show a balance larger than the amount you are allowed to send, and it is the single most common explanation for a transfer that will not go through.

## What the reserve is for

Every account on the XRP Ledger occupies space in a ledger that every node keeps a copy of. The reserve is the network's way of making that space cost something, so creating accounts is not free and the ledger cannot be filled with empty entries at no cost. Hold the reserve, and the account persists; release the account, and the reserve returns to you.

That framing answers the question people actually ask, which is "where did my XRP go". It went nowhere. Part of the balance is simply earmarked while the account exists, and the same XRP can be recovered by closing the account properly rather than by sending a payment.

## Two numbers, not one

Each account has a base reserve, and each object the account owns adds a further requirement. Trustlines are the objects most people meet: every trustline the account holds raises the total it must keep. An account with no trustlines needs less held back than one with five.

| What the account owns | Effect on the reserve |
|---|---|
| The account itself | Base reserve, always |
| Each trustline | Adds a per-object requirement |
| Each offer on the exchange | Adds a per-object requirement |
| Nothing extra | Base reserve only |

This is why two accounts with the same balance can show different spendable amounts. The difference is not a bug and not a fee; it is the objects the account owns.

## Balance, available, and spendable

Wallets use different words for the same three quantities, and the mismatch causes most of the confusion.

- **Balance** is what the ledger says the account holds in total.
- **Reserve** is the part that must stay while the account exists.
- **Available** is the balance minus the reserve: what you can actually send.

A wallet that shows only the balance invites the question in this article's title. A wallet that shows available as well makes the reserve visible, which is why OSM Wallet displays both rather than a single number.

## Why a payment is refused when you have XRP

A payment that would leave the account below its reserve is not valid, so the ledger rejects it. The wallet is passing on the ledger's rule, not imposing one of its own. The fix is to send a smaller amount, or to close the account if the goal is to move everything.

There is also a transaction fee, which is separate from the reserve and much smaller. A refusal is nearly always the reserve; a fee is nearly never the reason. The two are separated in [What an XRP transaction actually costs](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-fees-when-sending-from-osmwallet.md).

## Recovering the reserve

The reserve comes back when the account stops existing. That means closing the account: clearing its trustlines and token balances, then deleting it, with the remaining XRP sent to another account you control. It is a deliberate operation, not a cleanup task, and it is irreversible.

If you are emptying an account rather than closing it, the reserve stays held. That is the choice behind the question in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md), and the closing procedure is in *Deleting an account and recovering the reserve*.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows the balance the ledger reports alongside the available amount, so the reserve is visible rather than implied, and it supports closing an account so the reserve can be recovered. It does not set the reserve; the ledger does.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page. If a reserve figure in an older guide differs from what you see, the guide is older than the network.

## What people get wrong about it

Three misconceptions account for most support questions. The first is that the reserve is a fee paid once: it is held, not spent, and it returns on closing. The second is that it is set by the wallet: it is a network parameter, the same for every wallet. The third is that adding trustlines is free: each one raises the requirement, which is why an account full of tokens can have almost nothing spendable.

If you have just funded an account and it shows a balance with nothing available, that is the base reserve doing exactly what it should, and [Activating an XRP Ledger account](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/activate-an-xrp-ledger-account-osmwallet.md) covers the sequence that avoids it. If the available amount is not merely reduced but zero, *Why the wallet shows zero available XRP* works through the causes in order.

### FAQ

### Is the XRP reserve a fee?

No. A fee is spent and gone; the reserve is held while the account exists and returns when the account is closed. Nothing is paid to the wallet or to the network for holding it.

### Why can I not send my whole balance?

Because the account must keep its reserve, plus any requirement for trustlines or offers it owns. Sending everything would leave less than the minimum, and the ledger rejects such a payment.

### Do I get the reserve back?

Yes, when the account is closed properly: trustlines and tokens cleared, remaining XRP sent to a destination you choose, then the account deleted. Closing is irreversible, so do it deliberately.

### Does the reserve change?

The reserve is a network parameter and can be adjusted over time, which is why documentation quotes it as a current figure rather than a constant. Your wallet displays what the ledger currently requires.

### Do trustlines really cost reserve?

Yes. Each trustline or offer the account owns adds to the amount that must stay held. That is why an account holding several tokens can show a healthy balance and very little available.
