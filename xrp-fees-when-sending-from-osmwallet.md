<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# What an XRP transaction actually costs

An XRP payment costs a network fee that is tiny, plus nothing to the wallet. The fee is not the reserve, and confusing the two is why people believe sending XRP is expensive. The reserve is XRP held while an account exists; the fee is XRP destroyed when a transaction is validated. Only one of them leaves you.

## The fee is not the reserve

| | Network fee | Reserve |
|---|---|---|
| Paid per transaction | Yes | No, held while the account exists |
| Where it goes | Destroyed by the network | Stays in your account |
| Recoverable | No | Yes, when the account is closed |
| Size | A fraction of an XRP | The larger figure you see unavailable |

Almost every "why is the fee so big" question is really the reserve row. If the amount you cannot send is large and does not change between attempts, that is the reserve, covered in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md). The fee changes with network conditions and is small in absolute terms either way.

## How the fee is set

The ledger has a minimum fee, and under load the requirement rises: the network asks for slightly more to prioritise a transaction when many are competing. A wallet typically offers a sensible default and lets the user raise it if a payment needs to go through during congestion.

Raising the fee is never necessary in normal conditions and never rescues a payment that is malformed for another reason. A payment refused for reserve reasons will be refused at any fee.

## What the wallet does and does not charge

OSM Wallet does not take a cut of your payment. It submits a transaction you signed, with a fee the ledger requires, and that is the whole cost. There is no subscription, no per-send charge, and no spread applied to a transfer between two addresses.

The exception is buying XRP inside the wallet: that goes through a provider whose price and fees are theirs, described in [Buying XRP inside the wallet](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/buying-xrp-inside-osmwallet.md). That is a purchase, not a transfer, and the cost structure is completely different.

## Reading the fee before you sign

Every wallet surfaces the fee somewhere in the confirmation step, and it is worth knowing what the number means before a payment is signed rather than after. A fee that matches the ledger minimum is the normal case. A fee noticeably above it means either the network is busy or the wallet's default is conservative, and both are harmless.

What is not harmless is a fee expressed as a percentage of the amount. The ledger fee does not scale with the payment, so a large transfer and a small one cost the same to send. If a screen quotes a percentage, you are looking at a provider's charge, not a network cost.

That distinction is the practical version of the whole article: the ledger charges for the transaction, not for the value moving through it, and any cost that grows with the amount came from somewhere else.

## Where larger fees really come from

Three cases produce a cost that is not the network fee.

**Exchange withdrawals.** The service charges its own withdrawal fee, which has nothing to do with the ledger and is often far larger. It is disclosed on the withdrawal page.

**Buying inside a wallet.** A provider's spread and processing fee, again unrelated to the ledger fee.

**Network congestion.** The ledger's minimum rises temporarily. It returns when the queue clears, and it never approaches the reserve.

A fourth case is not a fee at all: a wallet showing a balance that cannot be spent, which is the reserve and is explained in *Why the wallet shows zero available XRP*.

## Why the last payment out is smaller

Because the fee is spent on top of the amount sent, a payment of exactly the available amount fails by the fee. That is why the sendable figure is the balance minus reserve minus fee, and why a small residual often remains after a "send everything" attempt. The arithmetic is in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md).

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows the fee with the transaction before you sign, so the cost is visible rather than inferred, and it displays the available amount so the reserve is not mistaken for a charge.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; fee display differs between builds, so compare the amounts rather than the labels.

If a payment will not go through at all, *When the wallet will not send the whole balance* sorts the refusal, and *Destination tags and memos, without the mistakes* covers the other common reason a send is held up.

### FAQ

### How much does sending XRP cost?

A fraction of an XRP in network fee, and nothing to the wallet. The exact figure is shown before you sign and moves with network conditions.

### Is the fee the same as the reserve?

No. The fee is destroyed per transaction; the reserve is held while the account exists and returns when the account is closed.

### Why does my exchange charge more than the network fee?

Because it is charging its own withdrawal fee, which is a business decision, not a ledger cost. It is shown on the withdrawal page before you confirm.

### Can I make a payment with no fee at all?

No. Every validated transaction costs a fee, though the minimum is small. A wallet that appeared to charge nothing would be paying it for you.
