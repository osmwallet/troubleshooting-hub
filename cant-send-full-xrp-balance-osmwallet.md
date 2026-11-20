<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# When the wallet will not send the whole balance

The ledger rejects any payment that would leave an account below its reserve, so the last transaction out of an account has to be smaller than the balance. That rejection is the rule working, not a fault. There are exactly two legitimate ways past it: leave the reserve behind and keep the account, or delete the account and sweep everything.

## What the refusal is actually saying

A wallet that will not send the whole balance is passing on a pre-validation failure. The transaction is malformed before it is submitted: amount plus fee would drop the balance under the minimum the account must hold. Nothing has been sent and nothing has been lost, which is why trying again with the same amount fails identically. A payment that would breach the reserve is refused before submission, so no fee is charged. The reserve amount is set by the network and changes only through a ledger amendment.

The two figures involved are the reserve and the fee. The reserve is held while the account exists, described in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md); the fee is spent and is much smaller, covered in *What an XRP transaction actually costs*. A refusal is almost always about the reserve.

## Route one: leave the reserve

Subtract the reserve from the balance, subtract a small margin for the fee, and send that. The account stays active with its reserve intact.

This is the right route when the address still receives payments, when other people have it saved, or when you are not certain you will never need it again. The cost is that a small amount stays behind, permanently unusable until the account is closed.

## Route two: delete the account

Deleting is a single transaction that sends the whole remaining balance, reserve included, to a destination and removes the account. It is how the reserve itself leaves the wallet.

The preconditions are what people miss: no trustline may hold a token balance, empty trustlines must be removed, and outstanding offers must be cancelled. A delete attempted before that is rejected, usually with an error that does not mention trustlines. The full sequence is in [Deleting an account and recovering the reserve](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-delete-account-recover-reserve.md).

Deleting is irreversible. If the address matters to anyone, route one is the safer answer regardless of the reserve.

## Why the two are not interchangeable

| | Leave the reserve | Delete the account |
|---|---|---|
| Amount moved | Balance minus reserve minus fee | Everything, minus the fee |
| Account afterwards | Active and able to receive | Gone |
| Reversible | Yes, it is just a payment | No |
| Token balances | Can stay | Must be cleared first |
| Good for | A working address | A finished one |

Choosing wrongly is the expensive mistake here: someone who deletes an address that still receives payments has to tell every sender, and someone who leaves the reserve on an address they will never use has locked a small amount for nothing.

## When the shortfall is larger than expected

If the gap between balance and sendable amount is much bigger than a reserve, the account owns things that raise the requirement. Each trustline adds to it, and each open offer adds to it. An account full of token trustlines can have most of its balance unavailable.

In that case the order is: move token balances out, remove the empty trustlines, cancel the offers, then either send what remains or delete. Removing trustlines alone raises the available amount without touching the account's existence, which is often enough.

## What does not help

Sending twice in quick succession does not work around the rule; the second transaction fails the same way. Lowering the amount by a rounding error does not work either, because the fee pushes it back under. And a wallet with a "send maximum" control is not bypassing anything: it performs the same subtraction, and the residual afterwards is the fee's remainder.

A payment refused for a missing destination tag is a different refusal that looks similar and is covered in [Destination tags and memos, without the mistakes](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/destination-tags-and-memos-in-osmwallet.md).

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It reports the available amount alongside the balance so the sendable figure is visible before a payment is attempted, and it supports deleting an account so the reserve can be recovered when the address really is finished with.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; the exact wording of a refusal message differs between builds, so compare behaviour rather than text.

For the arithmetic in full, *Sending your full XRP balance*. For a wallet showing nothing available at all, *Why the wallet shows zero available XRP*.

### FAQ

### Why will my wallet not send everything?

Because the account must keep its reserve. The ledger rejects a payment that would leave less than that, so the sendable amount is always smaller than the balance.

### Is there a setting to override it?

No, and there should not be. The rule belongs to the network, not to the wallet, so no setting can permit a payment the ledger will refuse.

### How much will be left behind?

The reserve plus the fee's remainder, normally a fraction of an XRP on top of the reserve. The available figure in the wallet is the exact amount you can send.

### Can I empty the account without deleting it?

No. Emptying means the balance is all reserve, which is the state that makes the account exist. Only deleting moves the reserve.
