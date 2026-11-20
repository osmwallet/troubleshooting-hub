<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Why the wallet shows zero available XRP

Zero available almost always means the balance is entirely reserve, the account owns something that raises the reserve, or the wallet is reading a different account than the one you funded. It is rarely a lost balance: the ledger is showing the account exactly as it is, and the number is telling you that none of it is currently spendable.

## Read the two numbers first

Before changing anything, distinguish three states.

| What you see | What it means |
|---|---|
| Balance 0, available 0 | The account is unfunded, or you are on the wrong network or account |
| Balance small, available 0 | The entire balance is reserve; nothing can be sent |
| Balance normal, available 0 | Trustlines or offers are consuming it, or the wallet is misreading the account |

The first row is a setup question, the second is arithmetic, and the third is the only one likely to be a wallet problem. Sorting which row you are in saves most of the work.

## Cause 1: the account is not funded

An address exists as soon as a key is generated, but the account does not exist on the ledger until XRP is sent to it. Until then there is nothing to display, and zero available is correct rather than broken. Activation is covered in [Activating an XRP Ledger account](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/activate-an-xrp-ledger-account-osmwallet.md).

A payment that arrived but shows nothing is the same cause seen from the other side: either the amount was below the reserve, or the payment has not validated yet.

## Cause 2: the whole balance is reserve

A first deposit that lands at or just above the base reserve produces an account that exists and can send nothing. The fix is a small additional deposit, not a support ticket. The arithmetic is in *The XRP reserve, explained without the confusion*.

This is the most common zero available in practice, because the person has just funded the account with the minimum they were told about.

## Cause 3: tokens and trustlines are holding it

Each trustline the account owns raises the reserve requirement. An account holding several tokens can show a healthy balance and no available XRP at all, which looks alarming and is entirely normal. Removing the trustlines you no longer need releases the per-object amount while keeping the account alive. The release shows up once the next ledger validates, so the available figure can lag a few seconds behind the removal.

If the tokens themselves are the goal, sending them out may free more than removing trustlines alone. The order and the constraints are in [Issued tokens and TrustLines in practice](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/issued-tokens-and-trustlines-in-osmwallet.md).

## Cause 4: the wallet is showing another account

Two mistakes produce this. The first is the testnet: it is a separate ledger, the same address there has a different and usually empty account, and the switch is easy to leave flipped. The second is a wallet holding several accounts where the selected one is not the funded one.

Switching back to mainnet and checking the address against the one you funded resolves both. The network switch is described in *Switching between testnet and mainnet*, and the multi-account case in *Read-only imports: what you can and cannot do*.

## Cause 5: the display is behind the ledger

A balance that has not refreshed after a deposit is a stale read, not a lost payment. Reopening the wallet re-queries the ledger; if the number is still zero, check the transaction itself rather than the wallet, because the ledger is the authority on whether the payment landed.

That check also settles the difference between "the wallet is wrong" and "the payment never arrived", which are very different problems with very different next steps.

## Why it is rarely a bug

The available figure is a subtraction the wallet performs on numbers the ledger returns. When those numbers are right, the subtraction is right. That is why a zero here is nearly always a statement about the account, and why the useful diagnostic question is not "why is the wallet broken" but "what does this account own, and on which network".

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows the balance and the available amount side by side and displays the active network, so a reserve-only account and a testnet view are both visible rather than implied. It also manages trustlines, which is what the third cause above requires.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page; a build older than the one described in guides may lay out these figures differently.

If the goal is to move what is left rather than to understand it, [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md) and *When the wallet will not send the whole balance* cover the two routes.

### FAQ

### Is my XRP gone if available shows zero?

No. Available is a subtraction, not a separate holding. The balance is still on the ledger; the question is what is holding it back.

### Why did available drop when I added a trustline?

Because each trustline raises the amount the account must hold. The XRP has not moved; more of it is now required to stay.

### Can a zero available balance be a network problem?

It can be a stale read, which a refresh fixes, or a testnet view, which a network switch fixes. A persistent zero with a normal balance means objects on the account.

### Does deleting the trustline give the XRP back?

It releases the reserve that trustline required, so the available amount rises. The tokens held on it have to be moved first.
