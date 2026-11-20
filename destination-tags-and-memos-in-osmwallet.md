<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Destination tags and memos, without the mistakes

A destination tag is a number attached to a payment that tells the receiving account which customer the money belongs to. It exists because exchanges and custodians receive everyone's deposits at one shared address. Send to your own wallet and there is no tag to enter; send to a service that gave you one and omitting it is the mistake that strands deposits.

## Why tags exist at all

An XRP Ledger address is an account, and an account cannot be split into sub-accounts. A custodian with a hundred thousand customers would need a hundred thousand funded accounts, each holding a reserve. The tag solves that: one address, one account, and a number in the payment that the custodian's ledger uses to credit the right person.

So the tag identifies **you** at **their** address. It is not a password, not a security feature, and not something your own wallet needs in order to receive.

## Tag, memo, and invoice

Three things get confused, and only one of them affects whether a deposit is credited.

| Field | What it is | Where it matters |
|---|---|---|
| Destination tag | A number identifying the recipient's customer | Custodial deposits and withdrawals |
| Source tag | A number identifying the sender | Rarely required by anyone |
| Memo | Free-form data carried with the payment | Invoices, references, business records |

A memo does not substitute for a tag. A custodian crediting by tag will not read a memo, and a payment with the right memo and no tag lands in the same unallocated pool as a payment with nothing attached.

## Getting it right in both directions

**Sending to a service.** The withdrawal page or deposit page gives you an address and, where needed, a tag. Copy both. If the service shows a tag and the wallet has an empty tag field, the payment is incomplete. The wider path from an exchange to this wallet is in [Moving XRP from an exchange into your own wallet](https://github.com/osmwallet/beginner-explainers/blob/HEAD/moving-xrp-from-an-exchange-into-osmwallet.md).

**Receiving from a service.** If you are withdrawing to your own OSM Wallet, leave the tag empty unless something explicitly tells you to use one. Many services pre-fill a tag field, and a tag sent to an account that does not expect one is harmless, but a tag you invent is a datum nobody reads.

**Test first.** A small first payment proves the address, the tag and the path in one go, and it settles the reserve question at the same time: [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md). The habit is worth keeping for every new destination, and the first-run sequence in *First run: the setup checklist* ends with exactly this check.

## When the tag is missed

The payment succeeds on the ledger; the XRP left your account and arrived at theirs. What fails is the crediting step inside the custodian, which cannot tell whose deposit it is.

The recovery route is the custodian's support process, and it depends entirely on them: some credit it once you prove the transaction, some charge a fee, some will not act at all. Nothing in your wallet can reverse the payment, because on the ledger it was valid and complete.

That asymmetry is worth internalising. A missing tag is not a failed transaction; it is a successful transaction with a missing label, and the label is the only thing that was ever going to identify you. A payment with no tag carries nothing the custodian can read against your account.

## What a tag is not

It is not a secret, and it does not protect the payment. The tag travels inside the payment itself, so it is visible to anyone who later reads that transaction. Anyone reading the ledger sees the tag. It is a reference number written in public, which is exactly its purpose and exactly its limit.

It is also not a destination. A tag with the wrong address sends to the wrong account entirely, and a correct address with the wrong tag credits the wrong customer, which is worse in some ways because the custodian has to untangle it.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Its send screen carries the destination tag field, so a payment to a custodian can include the number the custodian gave you, and it shows the details before signing so the tag can be checked rather than assumed.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; if a guide shows a field your build does not have, the build is the thing to check.

Related reading: [What an XRP transaction actually costs](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-fees-when-sending-from-osmwallet.md) for what the payment costs, and *Accepting XRP payments as a merchant* for the merchant side, where you are the one issuing tags.

### FAQ

### Do I need a destination tag to receive XRP?

No, not in your own wallet. A tag is for shared custodial addresses, where it tells the custodian which customer the deposit belongs to.

### What happens if I forget the tag?

The payment still completes, but the custodian cannot attribute it. Recovery depends on their support process and frequently takes weeks.

### Is a memo the same as a tag?

No. A memo is free-form data; a tag is the number the recipient uses to credit the right account. Sending a memo instead of a tag does not fix a missing tag.

### Can I cancel a payment sent without a tag?

No. Once validated it is final. Contact the receiving service with the transaction details and follow their process.
