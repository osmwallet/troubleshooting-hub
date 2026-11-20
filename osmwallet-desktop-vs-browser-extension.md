<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Desktop app or browser extension?

The desktop app is the workspace: full window, complete account management, and a key store that the browser cannot reach into. The browser extension is the same account with signing available inside web pages. They hold the same kind of secret; the difference is what surrounds it. Choose by what you are doing, not by which one sounds safer.

## What each one is for

**Desktop app.** Sending, receiving, trustlines, the exchange, and everything that benefits from space. It runs as its own process, unaided by the browser, and it is the natural place to do anything involving several steps.

**Browser extension.** Connecting to a site that asks for an address or a signature, without copying addresses between windows. It exists because web applications need a signer that is not the web page itself.

| | Desktop app | Extension |
|---|---|---|
| Full account management | Yes | Limited |
| Signs inside a web page | No | Yes |
| Exposed to browser extensions and page content | No | Yes, in principle |
| Works with the browser closed | Yes | No |
| Convenient for daily small payments | Less so | Yes |

## The security difference, stated without drama

Both store keys locally. The meaningful difference is the environment: a browser runs code from every site you visit, along with other extensions, and the wallet's own extension shares that process space. That is a bigger attack surface than a standalone application, and it is the reason the extension is best treated as a convenience layer rather than a vault.

That is not a claim that the extension is unsafe. It is a claim that its surroundings are busier, and that the same discipline applies with less margin for error.

## Which to use when

Use the desktop app for anything that changes the shape of the account: creating it, restoring it, adding or removing trustlines, and large transfers. Use the extension for the small, frequent interactions where copying an address into a site is the riskier alternative.

If you only ever do one thing, install the desktop app. It covers every operation, and the extension adds convenience rather than capability.

## Running both

Two independent installs each generate or import their own key store, so "the same account" means the same phrase restored in both places, not a shared file. That has a consequence worth stating: restoring in the second place is a second copy of the key, and it needs the same care as the first.

Keeping both in sync is manual by nature, because nothing is stored on a server. What one instance knows about the ledger it knows from the ledger, so balances agree; what it knows about your phrase it knows locally, so that part is duplicated rather than shared.

## Migrating between them

Moving from one to the other is a restore, and a restore is a phrase operation. That means typing the phrase into software, which requires the usual precaution: on a machine you trust, in a wallet you opened yourself, with nobody asking you for it.

After restoring, confirm the address matches the original before relying on it, and check the trustlines came across, covered in [What happens to your TrustLines after an import](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/trustlines-after-importing-a-seed-osmwallet.md).

## On a shared or borrowed computer

Install neither on a machine someone else administers. The key store lives in your user profile, so another administrator of that machine can reach the files, and a wallet you cannot control the surroundings of is not really yours.

If a shared machine is the only option, treat it as a temporary view rather than a home: use it to check a balance only if you can do so without entering a phrase, and do the real work elsewhere. The phrase rules in [Protecting a seed phrase you cannot reset](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/protecting-an-xrp-seed-phrase-osmwallet.md) are stricter than usual in this setting, because there is a second person with access to the same disk.

## What people get wrong

The common error is assuming the extension and the desktop app share a wallet file, then being surprised that a new account created in one does not appear in the other. The second is assuming the extension is protected by the browser's password manager, which it is not: the phrase is a separate credential and needs separate storage.

A third is leaving the extension installed in a browser profile used for everything, including sites of unknown provenance. Profiles are cheap; separate ones are worth the small inconvenience.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet shipped as a desktop application and as a browser extension. Both keep keys locally, both sign on your machine, and neither holds a server-side copy; the desktop build carries the full set of account operations while the extension provides signing in the browser.

It is actively maintained, and both builds come from the GitHub releases page, so "current" means the same thing for each. Which browsers the extension supports is a separate question, covered in [Which browsers the extension runs in](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/does-osmwallet-work-in-firefox.md).

For the setup path, *First run: the setup checklist*; for the safety framing, *Is OSM Wallet safe to use?*.

### FAQ

### Do the desktop app and the extension share a wallet?

Not automatically. Each install has its own key store, so the same account appears in both only if you restore the phrase in both.

### Which is more secure?

The desktop app has the smaller attack surface, because it is not loaded alongside web content. Neither is safe if the machine is compromised.

### Can I use only the desktop app?

Yes, and it covers every operation. The extension adds convenience for sites that need a signer, not extra capability.

### Does uninstalling one affect the other?

No. They are independent installs with independent key stores, so removing one leaves the other untouched.
