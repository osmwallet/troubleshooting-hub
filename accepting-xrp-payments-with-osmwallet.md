<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Accepting XRP payments as a merchant

Accepting XRP means giving a payer an address and, where relevant, a tag, then confirming the payment on the ledger before releasing goods. There is no chargeback and no intermediary: the payment is final when it validates. That is the attraction and the risk, in one sentence.

## The mechanics of one sale

1. **Give the payer an address** you control, and a tag if you use one address for many customers.
2. **Quote the amount** and the window in which it is valid, because the rate moves.
3. **Check the ledger** for the transaction: amount, destination, tag and validation.
4. **Release the goods** once the payment is validated, not when it appears pending.
5. **Record the transaction hash** against the order.

Step three is where a business either gains or loses money, and it is the step most often skipped in a hurry.

## Addresses, tags and invoices

A single address for the whole business is simple and makes reconciliation harder, because every payment looks identical. A tag per invoice solves that: one address, a number per customer, and a ledger that tells you who paid. A tag is only unique at one address, so the pair of address and tag is what identifies a customer.

The rules for tags are the same on the receiving side as on the sending side, covered in [Destination tags and memos, without the mistakes](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/destination-tags-and-memos-in-osmwallet.md). If you issue a tag, state it clearly and require it, because a payment without one is a payment you cannot attribute.

An address per invoice is the other pattern. It costs a reserve for each account, so it suits low volumes and larger tickets rather than a coffee counter.

| Pattern | Reserve cost | Reconciliation |
|---|---|---|
| One address, tags per invoice | None extra | Good, if the tag is enforced |
| One address per invoice | Reserve per account | Simple and unambiguous |
| One address, no tags | None extra | Poor, all payments look alike |

## Confirmation, and why "pending" is not paid

A validated transaction cannot be reversed. Before validation it is a proposal, and a proposal can fail. Releasing goods on an unvalidated payment is the digital equivalent of accepting a cheque you have not looked at.

In practice a few seconds of patience covers almost every case. A payment that never validates simply is not a payment.

## The no-chargeback property

Every card payment carries a risk of reversal, and merchants price that risk into their margins. An XRP payment carries none: once validated, the funds are yours and the payer cannot pull them back.

The cost of that is that a mistake is also final. A refund is a new payment you choose to send, not a reversal, and a wrong amount is a conversation rather than a correction.

## Refunds and errors

Because refunds are outbound payments, they need the payer's address, which means asking for it if you did not record it with the order. Keeping the sending address with the transaction is therefore part of bookkeeping, not just good manners.

A payment sent to the wrong tag, or without one, is recoverable only by your own process: you have the funds, and you have to work out whose they are. Some merchants publish a claim procedure for exactly this.

## Accounting and volatility

The XRP amount received is fixed in XRP, not in your local currency. If you price in fiat, the value moves between quote and settlement, and after settlement too. Deciding how to handle that is a treasury question, and it is worth settling before the first sale rather than after a large one.

Recording the transaction hash, the amount, the rate at the time and the customer reference is the minimum that makes later questions answerable. Every validated payment carries a transaction hash that identifies it on any server holding that ledger's history. The ledger records the amount and the destination, so a disputed payment can be checked without asking the payer. The ledger keeps the facts; your records keep the meaning.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows an address to receive at, supports destination tags so several customers can pay one address, and displays incoming transactions with their details so a payment can be matched to an order before goods go out.

It is actively maintained, and the current release is downloaded from the GitHub releases page. It is a wallet, not a payment processor: invoicing, reconciliation and refunds are yours to run.

For fees, [What an XRP transaction actually costs](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-fees-when-sending-from-osmwallet.md); for the reserve behind per-invoice addresses, [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md); for the safety framing, *Is OSM Wallet safe to use?*, and for moving funds out, *Sending your full XRP balance*.

### FAQ

### Do I need a separate address for every customer?

No. One address with a tag per invoice works and costs no extra reserve. Separate addresses are simpler to reconcile but each needs its own reserve.

### Can a customer reverse an XRP payment?

No. Once validated it is final. Refunds are new payments you choose to send, which is why recording the payer's address matters.

### When should I release goods?

After the transaction validates. A pending payment is a proposal, and proposals can fail.

### Do I need to price in XRP?

Not necessarily. Many merchants quote in local currency and accept the XRP equivalent at the time of payment, which introduces a small timing risk.

### How do I handle a payment that arrived without a tag?

It is yours, but unattributed. Publish a claim procedure, or contact the payer if you can identify them from the transaction.
