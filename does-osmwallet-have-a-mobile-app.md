<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# The mobile question, answered plainly

There is no mobile build you can install. OSM Wallet runs on Windows, macOS and Linux as a desktop app, and in Chrome as an extension; the site's download page includes a Mobile card listing iOS and Android, but that card's button is not a working download, and the site's own FAQ answers the same question by saying the wallet is available on desktop and in Chrome. Until a mobile build is actually published, anything on an app store using this name is not from the project.

## What the site actually shows

Two pages disagree in emphasis, and both are worth reading before you download anything.

The download page presents four cards: Windows, macOS, Linux and Mobile. The first three link to installer files. The fourth lists "iOS and Android" and offers a button that does not lead to a file, which is why clicking it does nothing useful.

The FAQ is blunter. It says the wallet is available today on desktop and in Chrome, and that a mobile app will be announced on the site. Taken together, the position is clear enough: desktop and Chrome now, mobile not yet, and no build to install while that remains true.

| Claim | Verified on the site |
|---|---|
| Desktop app for Windows, macOS, Linux | Yes, three installers |
| Chrome extension | Yes, documented as a Chrome extension |
| iOS app available to download | No working link |
| Android app available to download | No working link |
| App store listing from the project | None found |

## Why the fourth card is the dangerous one

A card that says "iOS and Android" is an invitation to go looking, and looking is where people get hurt. Store listings can use any icon and any name; the publisher field is the only part that is hard to copy convincingly.

The pattern is old and reliable: a wallet gets attention, lookalike apps appear within weeks, they ask for a recovery phrase during "import", and the balance is gone before the user notices the app had no reason to want a phrase.

## What to do with XRP on a phone today

Two honest options, neither of which involves installing something called OSM Wallet on a phone.

**Keep the wallet off the phone.** Use the desktop app for anything that needs a key, and treat the phone as a way to read information rather than to sign. This is the position the site's own FAQ describes.

**Use a mobile wallet you have verified yourself**, understanding it is a separate product with a separate phrase and a separate backup. Its phrase is not your OSM Wallet phrase, and restoring your OSM Wallet phrase into it would create the same account in a second place with a second copy of the key.

What does not work is installing an app because the icon matches.

## Travelling with the wallet

The setup that travels is the same one that stays home: the phrase offline and away from the device, the wallet on a machine you control. A laptop with the desktop app is the travel case; a second browser profile with the extension is the light option, described in [Desktop app or browser extension?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-desktop-vs-browser-extension.md).

Copying the phrase into a phone note so it is available on the road converts an offline backup into a synced one, which is the worst version of the idea.

## When a mobile build does appear

The checks will not change. Install from the project's own link, confirm the publisher matches the project, check the version against the download page, and test the restore before funding anything. Those habits apply on every platform, which is why [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md) is worth reading even if you never install on a phone.

Nothing about a small screen makes a wallet safer. The key is the key, and the phrase rules in [Protecting a seed phrase you cannot reset](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/protecting-an-xrp-seed-phrase-osmwallet.md) do not relax because the device is convenient.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser, distributed through its GitHub releases page and its own download page. Nothing is held on a server, so there is no account to log into on a second device: the same wallet elsewhere means restoring the phrase there.

It is actively maintained, and the download page is the place to see what exists rather than a store search. Fake apps are covered in *Telling the real site from a lookalike*, the safety framing in *Is OSM Wallet safe to use?*, and what self-custody means in *What a non-custodial wallet actually means*.

### FAQ

### Is there an OSM Wallet mobile app?

Not one you can install. The site offers desktop installers and a Chrome extension; the mobile card on the download page does not lead to a file.

### Can I use the wallet in a phone browser?

No. The extension is a Chrome desktop extension, and a mobile browser cannot install it.

### Why does the download page show iOS and Android?

It advertises the platforms a mobile build would cover. The button is not a working download, so there is nothing to get from it yet.

### Is an app store listing for OSM Wallet genuine?

Assume not unless the project's own site links to it. Store names and icons are easy to copy; the publisher is the part that matters.

### How do I keep XRP safe while travelling?

Keep the phrase offline and the wallet on a machine you control. Do not copy the phrase into a phone note or a cloud app to make it convenient.
