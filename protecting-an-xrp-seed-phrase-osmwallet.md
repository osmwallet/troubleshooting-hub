<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Protecting a seed phrase you cannot reset

There is no reset. A recovery phrase is the wallet, and losing it loses the account; anyone who reads it owns the account. So the phrase has to exist offline in at least one place you control, in no place anyone else can reach, and in enough copies that one accident is survivable.

## What the phrase is

A recovery phrase encodes the private key for an account. Whoever has it can reconstruct the key and sign payments, with no further authentication. It is not a password, because a password can be changed once and a phrase is fixed for the life of the account.

That single property drives everything below. There is no reset link, no support process, and no second factor that saves you once the phrase is out.

## The storage rules

**Offline.** Paper or metal, kept physically. A phrase in a note, a screenshot, a document, a password manager or a cloud drive is one breach away from being someone else's.

**Two copies, two places.** A single copy is destroyed by a fire, a flood, a move or a tidy-up. Two copies in the same drawer share the same fate, so the places have to be genuinely separate.

**Legible in twenty years.** Faint pencil, a cramped margin or a coffee stain fails at exactly the moment it matters. Write it clearly, and check it a week later rather than a decade later.

**Not labelled.** A sheet headed with the wallet name and the account balance is an invitation. A plain sheet in a safe place is not.

| Method | Survives fire | Survives water | Survives discovery |
|---|---|---|---|
| Paper in a drawer | No | No | Only if hidden |
| Paper in a safe | Partly | Partly | Yes, if the safe is not opened |
| Stamped metal | Yes | Yes | Yes |
| Cloud note or photo | Yes | Yes | No, this is the failure case |

## Testing the backup

A backup nobody has tested is a hope. Before funding an account, restore the phrase into a fresh wallet and confirm it produces the same address; then delete that test wallet. If it does not, you have found the problem before it mattered.

Doing this requires typing the phrase into software, which is exactly the thing this article tells you not to do elsewhere. The distinction is that you opened this wallet yourself, offline if possible, and you are not being asked by anyone.

## Splitting, sharing, and inheritance

Splitting a phrase into parts kept in different places can protect against a single theft, but it introduces a new failure: a lost part loses the account, and a reconstructed phrase in the wrong hands loses it too. If you split, be certain the reconstruction instructions are unambiguous.

For inheritance, the problem is not storage but handover. Someone has to know the phrase exists, where it is, and what it is for, without that knowledge being enough to take it early. A sealed letter with a lawyer is a common answer; a note taped to the device is not.

## When the phrase is exposed

Assume immediate loss and act accordingly: create a new account, move the funds, and stop using the exposed one. Do not wait to see a suspicious transaction, because the attacker will take the balance at a moment of their choosing, which may be months later.

Creating the replacement account and moving funds is the same operation as any other send, covered in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md) for the last amount out, and in [Deleting an account and recovering the reserve](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-delete-account-recover-reserve.md) if the old account should cease to exist.

## What the phrase does not protect

It does not protect against a swapped address, because the attacker does not need your key if you send to theirs. It does not protect against malware that changes what you see. And it does not protect a balance left on a custodial service.

Storage and signing are separate problems. This article is about the first; the second is in [How XRP gets stolen, and what stops it](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/can-xrp-be-stolen-from-a-cold-wallet-osmwallet.md).

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It shows a recovery phrase once, during setup, and again only in a restore you initiate; it does not store a copy on any server, and it has no mechanism to reset or recover an account, because the phrase is the only credential.

It is actively maintained and distributed through its GitHub releases page. Whether the phrase you wrote down opens the account is something only a restore test can answer, and that test is worth doing once, early.

For the wallet-level safety picture, *Is OSM Wallet safe to use?*. For restoring on a replacement machine, *Restoring access after losing a device*.

### FAQ

### Can I change my seed phrase?

Not for an existing account. You can create a new account with a new phrase and move the funds, which is the only way to replace an exposed one.

### Is a photo of the phrase safe if the phone is locked?

No. Camera roll backups, cloud sync and account takeovers all defeat the lock, and a photograph is a digital copy of the key.

### How many copies should I keep?

At least two, in places that fail separately. One copy is a single accident away from total loss.

### What happens if I lose the phrase?

The account is unrecoverable. The XRP remains on the ledger, but nothing can sign for it, and no support process can help.

### Should I test the backup?

Yes, before funding the account: restore it into a fresh wallet, confirm the address matches, then remove the test wallet.
