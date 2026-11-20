<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Telling the real site from a lookalike

The real site is the one the project's own release page points to; a lookalike is everything else until proven otherwise. Phishing against wallet users does not break anything, it asks politely: a copy of the site, a slightly different domain, and a form that wants your recovery phrase. Recognising that pattern is a skill, not a setting; the wider picture of what a wallet can and cannot protect is in [Is OSM Wallet safe to use?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/is-osmwallet-safe.md).

## Why wallet users are targeted

A wallet holds a bearer asset. There is no chargeback, no bank to call, and no account recovery, so a single successful theft is final. That economics explains the effort put into the copies: they are cheap to make, and one visitor pays for thousands of attempts.

The copies also target a specific moment: someone who has just installed a wallet and is unsure what to do next is the most likely to type a phrase into a page that asks for it.

## The patterns worth knowing

**The domain that is almost right.** One letter different, a hyphen added, a different ending, or a word inserted. Reading a domain character by character is slower than glancing at it and is the only reliable method.

**The search advert.** Paid results can sit above the real site, and an advert's display text can look exactly like the real one while the link goes elsewhere. The address bar is the truth; the headline is not.

**The phrase form.** Any page that asks for your recovery phrase to "verify", "sync", "restore", "validate" or "migrate" a wallet is an attack. There is no legitimate version of that request.

**The support conversation.** Someone who messages first, offers help you did not ask for, and eventually needs your phrase, is running a script. Real support does not need the phrase, because it cannot do anything with it that you cannot.

**The download link.** An installer from anywhere other than the project's release page is unverified, whatever it claims. This is where a fake site does the most damage, because the file runs with your permissions.

## How to verify in practice

1. **Start from a bookmark you made yourself**, not from a search result and not from a link in a message.
2. **Read the domain in the address bar**, character by character, and confirm the ending.
3. **Check for a padlock**, understanding it means the connection is private, not that the site is honest.
4. **Compare against the release page**, which is the project's own pointer to its downloads and its site.
5. **Refuse any phrase request**, immediately and without discussion.

Step four is the one that settles it. A site that contradicts the release page is not the project's, however polished it looks. Bookmark the address once you have confirmed it, because a bookmark is the one entry point a paid advert cannot move.

## What a fake site always wants

The copies are consistent because the goal is consistent: they want the thing that lets them sign. That means the phrase, a wallet file, a private key, or a "verification" payment that is really a transfer.

| Asked for | Legitimate? |
|---|---|
| Recovery phrase, to verify or sync | Never |
| Wallet file or private key | Never |
| A payment to "activate" or "unlock" | Never |
| A download from the official release page | Yes |
| A tag when depositing at a custodian | Yes |

Anything in the first three rows ends the conversation. The distinction between the last two rows and the first three is the whole of this article.

## After a mistake

If a phrase was typed into a page, treat the wallet as compromised and move the funds to a new account from a different device, without waiting to see whether anything happens. The mechanics of emptying the old account are in [Sending your full XRP balance](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/send-max-xrp-balance-osmwallet.md). If an installer was run, assume the machine is untrustworthy and rebuild it before using a wallet on it.

Both responses are about speed. The attacker's advantage is that you keep using the wallet while deciding what to do.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Its restore flow asks for a phrase only when you start it yourself, from a wallet you opened, and its send screen shows the destination before signing so a hijacked address is visible.

It is actively maintained and distributed through its GitHub releases page, which is the reference to compare any other site against. The wallet cannot inspect the site you are reading; that comparison is yours.

For the installer check, see [Checking that your installer is the real one](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/verify-osmwallet-installer-checksum.md); for the phrase habits, *Protecting a seed phrase you cannot reset*; for the theft routes in general, *How XRP gets stolen, and what stops it*.

### FAQ

### What is the official OSM Wallet site?

The site the project's release page links to. Confirm it there rather than from a search result, an advert or a message, and bookmark the address you confirmed.

### Does the wallet ever ask for my seed phrase?

Only in a restore that you initiate yourself inside the wallet. Any other request, in a browser, a chat or an email, is an attempt to take your funds.

### Is a padlock in the address bar enough?

No. It means the connection is private, not that the operator is honest. Lookalike sites have padlocks.

### What if I already typed my phrase into a site?

Move the funds to a new account immediately, from a different device if you can. Do not wait for a suspicious transaction to appear first.
