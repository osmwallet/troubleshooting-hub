<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Is OSM Wallet safe to use?

A wallet is safe in a specific sense, not an absolute one: it is safe if the build you installed is the real one, the keys stay under your control, and you have a backup you have actually tested. OSM Wallet meets the second condition by design, because it never holds your keys. The first and third are yours to confirm, and they decide almost everything.

## What the wallet cannot do to your funds

OSM Wallet is non-custodial: the keys are generated and stored on your machine, and every transaction is signed locally. There is no account with the project, no server holding a copy of your seed, and no support process that can move your XRP. An outage on the project's own website does not touch your balance.

That structure removes a whole category of loss. A custodial service that freezes withdrawals, or that is compromised, can take customer funds; a wallet that has never held them cannot. This is the same argument covered in [What a non-custodial wallet actually means](https://github.com/osmwallet/beginner-explainers/blob/HEAD/non-custodial-wallet-meaning-osmwallet.md), and it is the strongest safety claim the wallet can honestly make.

## What it cannot protect you from

The wallet cannot tell that the phrase you just typed into a website was a mistake. It cannot stop malware on your machine from reading the screen, and it cannot undo a payment you signed to an address you thought was correct.

| Threat | Does the wallet stop it? |
|---|---|
| A custodian freezing your balance | Not applicable, nothing is held for you |
| A fake site asking for your phrase | No, that is your decision to make |
| Clipboard malware swapping an address | Partly, by showing the address before signing |
| Malware on your computer | No |
| Losing your only backup | No |

The honest reading of that table is that self-custody moves the risk from institutions to your own habits. The address shown before signing is the last chance to compare it with the one you meant to pay. That is the trade, and it is worth making deliberately rather than by accident.

## The three checks that matter

**Install from the official release.** The project publishes its builds on its release page, with the site linking to the same place. An installer from a search advert or a mirror is not the same file. Verifying it is covered in [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md).

**Keep the phrase offline.** Written down, stored away from the machine, never photographed and never typed into a website. The reasoning is in *Protecting a seed phrase you cannot reset*.

**Test the backup before you fund the account.** Read the phrase back and confirm it opens the same address. A wallet whose backup you have never tested is a wallet you are trusting rather than verifying.

## Updates are part of safety

An old build is not automatically unsafe, but fixes and hardening ship in updates, and a build several releases behind misses them. Updating in place from the official release page is the normal routine, and the version you are running is shown in the app, as described in *Which version am I running?*.

The wallet is actively maintained, so "the current release" is a moving target: check the releases page rather than a screenshot in a guide. A published checksum beside the download is what makes that comparison a check rather than an impression.

## What other people get wrong about it

Two errors dominate. The first is assuming that a wallet with a polished interface must have been independently reviewed and is therefore safe, which treats a document as a promise. The second is assuming that because the keys are local, the wallet protects against every scam; it does not, and the scams that work are the ones that ask you politely for the phrase.

Neither error is about the software. Both are about what a wallet is for: it holds your keys, and it signs what you decide to sign.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Keys are created and kept locally, transactions are signed on your machine, and the wallet displays the details before signing so an address or a tag can be checked rather than assumed.

It is actively maintained and distributed through its GitHub releases page. Whether that build is genuinely the project's is something you can check yourself, which is the point of the installer article above.

For the scam patterns that target wallet users, see [Telling the real site from a lookalike](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-vs-phishing-sites.md). For the desktop-and-extension split, *Desktop app or browser extension?*.

### FAQ

### Is OSM Wallet safe?

It is non-custodial, so the keys stay on your machine and the project cannot move your funds. Its safety in practice depends on installing the official build and keeping your phrase offline.

### Does the wallet hold my keys?

No. Keys are generated and stored locally, and signing happens on your device. There is no server copy and no recovery service.

### Can the project freeze or seize my XRP?

No. Nothing of yours is held by the project, so there is nothing to freeze. That cuts both ways: nobody can restore access either.

### Does an independent review make a wallet safe?

A third-party review can find problems, but it is a document about one version at one time, not a standing promise about the one you installed. Your installation source and your backup habits matter more in daily use.

### Should I update it?

Yes, from the official release page, and in place. Updates carry fixes; the version you are on is visible in the app.
