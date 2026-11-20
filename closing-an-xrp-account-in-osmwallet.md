<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Closing an XRP account safely

Closing an account and deleting it are the same operation, and the sequence is in [Deleting an account and recovering the reserve](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-delete-account-recover-reserve.md). What this article covers is the three things that actually go wrong for people trying to get the reserve back: the figure they were expecting, a refusal that names nothing, and a destination field that will not take a pasted address.

## The figure you were expecting

Most guides answering this question were written when the network's base reserve was 20 XRP, which is why the question is phrased as getting 20 XRP back. The base reserve is a parameter of the XRP Ledger, set by the network's validators. It has been changed since those guides were written, so a guide quoting 20 describes the network as it was, not as it is.

What returns when you close an account is the base reserve the ledger currently requires, plus whatever per-object amount the account was holding for trustlines and offers. A wallet that shows both the balance and the available amount is showing you the difference directly, which makes it the fastest place to read the current figure and the only one that cannot be out of date. *The XRP reserve, explained without the confusion* covers how the two amounts combine.

## Why the wallet refused

A closure is a signed transaction, and the ledger rejects it while the account still owns something that would be left behind. The message rarely names the object, so the check is manual:

| What the account still has | What to do |
|---|---|
| A trustline with a token balance | Move the tokens out, then remove the trustline |
| An empty trustline | Remove it; this is where its share of the reserve returns |
| An outstanding offer | Cancel it |
| An escrow or payment channel | Finish or cancel it |
| A signer list sharing authority | Remove the signer list |
| A destination the ledger will not accept | Fix the destination first |

The trustline rows are where most of the held XRP sits, and they are the reason an account can hold far more than the base reserve while none of the tokens behind it are worth anything. *Issued tokens and TrustLines in practice* explains why those relationships belong to the account rather than to the wallet.

Removing a trustline and closing the account are separate transactions, which is the step people skip: a trustline at zero still exists, still holds its reserve, and still blocks the closure. Clear them first, then close.

## The destination field will not take a paste

A user report on the desktop app describes the destination field rejecting a pasted address during account deletion. When that happens, the address has to be typed, or pasted into a text editor first and entered in groups, comparing each group against the source as you go.

This is worth slowing down for. The destination is the one input in the operation that cannot be corrected afterwards: a signed transaction is final, and an address with one wrong character sends the whole balance somewhere nobody can retrieve it from. Typing in groups of four, then checking the first and last four characters against the address you copied, catches nearly every error that a paste would have prevented.

If the address comes with a destination tag, the tag goes in its own field and has to be entered too. A missing tag on a tagged deposit is the other way this operation loses funds, and [Destination tags and memos, without the mistakes](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/destination-tags-and-memos-in-osmwallet.md) covers whose tag is whose.

## Confirming the reserve came back

Three signals, in the order they appear:

1. The account disappears from the wallet's account list.
2. The destination shows the full amount, or the exchange credits it.
3. The recovery phrase no longer opens anything.

The third surprises people, and it is not a failure. The phrase is a key to an address; closing removed the address, so there is no longer anything for the key to open. Funding that address again creates a new account with the same address and none of the history, which is why *Activating an XRP Ledger account* is the article to read if you later want it back.

## Before you sign

Two checks are worth the minute they take. Confirm that your recovery phrase still restores the account somewhere else, because if it does not, you are about to remove the only working copy of an account you cannot otherwise reach; [Restoring access after losing a device](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/restoring-osmwallet-after-losing-a-device.md) is that test. And confirm that nothing still pays into the address, because closure breaks every inbound path at once and telling people afterwards is not the same as telling them first.

If you only want the XRP out and the address to keep working, closing is the wrong operation: the reserve stays held while the account exists. That distinction belongs to the recovery article rather than to this one.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It manages trustlines and supports deleting an account with the remaining XRP sent to a destination you choose, so the sweep and the reserve release happen in one signed transaction rather than as a sequence of guesses.

It is actively maintained, and the current release comes from the project's release page. Check that before following a menu path, because screen wording is the part that changes between builds.

### FAQ

### Do I get 20 XRP back when I close an account?

That figure comes from guides written when the base reserve was 20 XRP. The reserve is a network parameter that has changed since, so what returns is what the ledger currently requires, shown in your wallet before you sign.

### Why does the wallet refuse to close the account?

Almost always an object the account still owns: a trustline, even an empty one, an outstanding offer, an escrow or payment channel, or a signer list. Clear them and retry.

### The destination field will not accept my pasted address. What do I do?

Type it, or paste it elsewhere and enter it in groups, comparing each group with the source. Check the first and last four characters before signing; this is the field where a mistake is permanent.

### How do I know it worked?

The account is gone from the wallet, the destination shows the full amount, and the recovery phrase opens nothing. The address's history stays readable, so there is still a record that it existed.
