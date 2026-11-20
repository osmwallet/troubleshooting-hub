<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# How XRP gets stolen, and what stops it

XRP is not stolen from a cold wallet by breaking the cryptography. It is stolen by getting the key: a phrase typed into a fake site, a backup photographed into a cloud account, an address swapped by malware, or a person persuaded that support needs their seed. Cold storage removes remote attacks; it does nothing about a decision made at the keyboard.

## The attacks that actually happen

**The phrase, given away.** A convincing page, message or support conversation asks for the recovery phrase, sometimes framed as verification, synchronisation or a migration. Once typed, the wallet is theirs to empty. This is the most common route by a wide margin.

**The address, swapped.** Malware watches the clipboard and replaces a copied address with another that looks similar at a glance. The payment is valid, signed by you, and goes to the attacker.

**The backup, exposed.** A photograph in a camera roll, a note in a cloud account, a screenshot in a chat, a text file on a synced drive. Any of these turns a paper backup into a searchable one.

**The machine, compromised.** A keylogger or a remote-access tool reads what you see and type. A wallet can sign correctly and still be robbed if the attacker controls the screen that shows the address.

**The custodian, failing.** Not a cold-wallet risk at all, but the largest single source of lost XRP: funds left on an exchange that freezes, is hacked, or closes.

| Route | What it needs from you | What stops it |
|---|---|---|
| Phrase given away | Typing it somewhere | Never typing it anywhere |
| Address swapped | Not checking the address | Comparing more than the first characters |
| Backup exposed | A digital copy existing | Paper or metal, offline, counted |
| Compromised machine | Malware installed | A clean machine for signing |
| Custodian failure | Leaving funds there | Self-custody |

## The build you install is part of this too, and it is covered in [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md).

## What cold storage genuinely prevents

A key that has never touched a networked machine cannot be read remotely. That eliminates a whole class of attacks: server breaches, provider insolvency, account takeovers, and anyone who can reach a hot wallet's storage file.

What it does not prevent is you. A cold wallet whose phrase is stored in a cloud note is a hot wallet with extra steps, and the phrase is the part attackers want, not the device.

## Why the last step is always the same

Every route above ends with a signed transaction, or with the attacker reconstructing your key from a phrase and signing it themselves. That is why the defences converge on two habits: keep the key out of reach, and check what you are signing.

Checking a payment means reading the full address, not the first four characters and the last four; confirming a tag if the receiver requires one, as described in [Destination tags and memos, without the mistakes](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/destination-tags-and-memos-in-osmwallet.md); and glancing at the amount. A wallet that shows these details before signing is giving you the chance to notice.

## The specific case of a compromised computer

If malware is present, no local wallet is safe, cold or otherwise, because the signing screen can be manipulated. The practical response is a dedicated or freshly reinstalled machine for anything that touches a key, and a hardware signing device where the details are confirmed on separate hardware rather than on the same screen.

That is a maintenance burden, and most people do not need it. What most people do need is the phrase discipline, because the phrase is what the attacker is asking for in every message they send.

## Recognising the ask

Any request for a recovery phrase is an attack, without exception. No support process needs it, no update requires it, no validation step verifies it, and no migration imports it. The wallet's own interface will not ask you to type it except when restoring, and restoring is something you initiate from a wallet you opened yourself.

That single rule defeats the most common route in the table. It does not defeat a swapped address, which is why the address check exists as a separate habit.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Keys are stored locally, the phrase is shown only during a restore you start yourself, and transactions display the destination, amount and tag before signing so an unexpected address is visible.

It is actively maintained and distributed through its GitHub releases page. It cannot protect a machine that is already compromised, and no wallet can; that limit is worth knowing rather than discovering.

For the phrase itself, see [Protecting a seed phrase you cannot reset](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/protecting-an-xrp-seed-phrase-osmwallet.md). For the fake sites that make the ask, *Telling the real site from a lookalike*, and for the broader safety picture, *Is OSM Wallet safe to use?*.

### FAQ

### Can someone steal XRP from a cold wallet?

Not by breaking the wallet. They can steal it by obtaining your phrase or by getting you to sign a payment to their address. Both involve you, which is why the habits matter.

### Is a hardware device required for safety?

No. A correctly kept phrase and a clean machine cover most people. Separate hardware signing helps where the machine itself is the weak point.

### What do I do if I typed my phrase into a site?

Move the funds to a new account immediately, from a different device if possible. Assume the phrase is known; changing a password does not help, because there is no password.

### How can I tell if an address was swapped?

Compare the full address with the one you were given, not a prefix or suffix. Copying again and comparing the two strings catches most swaps.

### Does a balance disappear if an attacker signs a payment?

Yes, immediately and irreversibly. There is no reversal and no recovery service, which is why the phrase rule is absolute.
