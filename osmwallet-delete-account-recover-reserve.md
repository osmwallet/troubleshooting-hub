<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Deleting an account and recovering the reserve

Deleting an account sends its remaining XRP to a destination you choose and removes the account from the ledger, which releases the reserve. It is irreversible: the address stops existing, its history stays readable, and reusing it means activating a new account. Do it when you want the reserve back, not as routine cleanup.

## What deleting actually does

The operation is a transaction signed by the account itself. It can only succeed when the account owns nothing that would be orphaned: no trustlines holding balances, no outstanding offers, no other obligations. When it succeeds, the remaining XRP, including the reserve, is sent to the destination in the same transaction.

This is why deletion feels like a payment with an extra effect. The recipient receives everything the account held, and the account ceases to exist. There is no separate step for the reserve; it is simply part of what is swept.

## The order of operations

1. **Decide the destination.** An account you control, or an exchange deposit address with the tag it requires.
2. **Clear trustlines with token balances.** Tokens must be sent or spent first; a trustline with a balance blocks deletion.
3. **Remove the empty trustlines.** This is where the per-trustline reserve is released, and it must precede the delete.
4. **Cancel outstanding offers**, if the account has any on the exchange.
5. **Confirm the amount** that will move is what you expect: balance minus the fee.
6. **Sign the delete** and check the destination one more time, because there is no undo.

Step two is the one that stops most attempts. A trustline holding even a tiny token balance prevents deletion, and the error message rarely says so in those words.

## When not to delete

Do not delete an account that other people pay to, unless you are prepared to tell them all. Do not delete an account whose recovery phrase you are unsure of, because the address cannot be recreated reliably later. And do not delete the last account you control in order to save a reserve: the reserve is worth less than an address that still works.

Deleting is also the wrong tool when the goal is only to empty the account. Emptying leaves the account funded with its reserve and still usable; deleting removes it entirely. That distinction is covered in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md). Consolidating several accounts is not what deletion does: each has to be cleared and swept on its own.

## What you lose, and what you keep

| Lost | Kept |
|---|---|
| The account's existence on the ledger | The address in your records, as history |
| Its ability to receive | The transaction history, still readable |
| Its trustlines | The XRP, now at the destination |
| Its settings, such as a regular key | The recovery phrase, which no longer opens it |

The last row is the one to think about before signing. The phrase does not restore a deleted account: importing it produces an address that no longer exists, and funding it again creates a new account with the same address but none of the history.

## Recovering the reserve without deleting

If you want the reserve back but need the address to keep working, you cannot have both: the reserve is the price of the account existing. What you can do is reduce the reserve requirement by removing trustlines you no longer need, which releases the per-trustline amount while keeping the account.

That is often the right intermediate step. An account with five old trustlines can free most of its held XRP by clearing them, and stay alive for the payments it still receives. Each removal is its own transaction with its own fee, so clearing five of them is five steps rather than one. If the account has never been funded in the first place, the place to start is [Activating an XRP Ledger account](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/activate-an-xrp-ledger-account-osmwallet.md).

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It manages trustlines and supports deleting an account with the remaining XRP sent to a destination you choose, so the reserve recovery happens as part of one deliberate operation rather than as a sequence of guesses.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; check that before following any procedure that names a menu.

For the reserve itself, see [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md). For the trustline step that blocks most attempts, *Issued tokens and TrustLines in practice*. For the safer alternative when you only want to empty the account, *Sending your full XRP balance*, and for a destination that needs a tag, *Destination tags and memos, without the mistakes*.

### FAQ

### Do I get all the XRP back when I delete an account?

The remaining balance, including the reserve, is sent to the destination you choose, minus the transaction fee. Anything held in tokens must be moved out first, or the delete will not be accepted.

### Can I undo a deleted account?

No. The account stops existing. Funding the same address again creates a new account with the same address and no history, and the old phrase is not a backup of anything.

### Why does deletion fail when I have no tokens?

Check for trustlines with balances, outstanding offers and a destination that is missing a required tag. Each of those blocks the transaction for a different reason.

### Is deleting an account the same as closing it?

Yes. Closing, deleting and removing an account are the same operation described in different words: clear what it owns, sweep the XRP, and the ledger removes the entry.
