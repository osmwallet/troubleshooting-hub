<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Checking that your installer is the real one

Compute the hash of the file you downloaded and compare it with the value published for that build. If the two strings are identical, the file you have is the file that was published. If they differ, do not install it: delete it, download again from the official page, and check once more.

That is the whole check, and it takes about a minute. What follows is how to run it on each system, where the value should come from, and what the result does and does not tell you.

## What a hash is

A hash function reads a file and produces a short fixed-length string from its contents. Change one byte anywhere in the file and the string changes completely; there is no way to adjust a file so the string stays the same. That is what makes it useful here: the published string is a fingerprint of one specific file, and your copy either matches it or does not.

The comparison is exact. Not "starts the same", not "looks similar". Two hashes that differ in the last character describe two different files, and the difference is the whole point.

## Where the published value should come from

The value has to come from the project, not from the file, and not from wherever you found the download.

- **The download page on the project's own site**, beside the file it describes.
- **The release listing** for the build, if the project publishes hashes with the release.

Both are first-party. A hash printed on a third-party mirror, in a forum post, or in a chat message proves only that someone typed it, and it is exactly the kind of thing an attacker would supply alongside a substituted installer.

One honest note about the current state of the documentation: not every build has a hash published next to it. If the build you downloaded has none, you cannot perform this check on it - and the correct response is to say so plainly rather than to install and hope. Ask for the value, or wait for a build that publishes one. A missing fingerprint is a reason to be careful about the source, not a reassurance that the file is fine.

## Computing it on each system

**Windows, in Command Prompt or PowerShell:**

```
certutil -hashfile osmwallet-installer.exe SHA256
```

In PowerShell, `Get-FileHash <path> -Algorithm SHA256` produces the same value with the algorithm named in the output. Ignore the spaces certutil inserts when comparing; the characters are what matter.

**macOS, in Terminal:**

```
shasum -a 256 ~/Downloads/<the-installer-file>
```

**Linux, in a terminal:**

```
sha256sum ~/Downloads/<the-installer-file>
```

Use the algorithm the project publishes. If the published value is a SHA-256 hash, compare it with a SHA-256 output; comparing across algorithms produces two different strings for the same file and tells you nothing.

## Comparing the strings without making a mistake

The failure mode here is human, not technical. A 64-character string is easy to misread, and a false mismatch sends people back to download a file that was already correct.

- Compare from the page you loaded yourself, not from a message or a screenshot.
- Do not compare a prefix, however long. Whole string or nothing.
- Beware line wrapping in a terminal: the value may break across two lines.
- If a tool uppercases the hash, case does not matter; the value does.
- Where the page offers a copy button, use it and paste beside the computed value rather than reading both by eye.

On a desktop, `Get-FileHash` and the page's value can be diffed by pasting both into a text editor and comparing the lines; anything simpler risks the eyeball comparison that this check exists to avoid.

## When it does not match

Do not install the file. Work through the causes in order:

1. **Was the download complete?** A connection that drops mid-file produces a different file. Check the file's size against the one the page lists, then re-download.
2. **Did you hash the right file?** Downloads folders accumulate copies, and hashing an older download of the same installer is a common false alarm.
3. **Is the value for this build?** A hash published beside a different release will not match, and a page mixing builds is a documentation problem worth reporting.
4. **Re-download from the official page** and check again. Do this before assuming anything worse.

If the new download still does not match, stop. Two mismatches in a row mean either the published value is wrong or the file you are receiving is not the one that was published. Neither is a situation to click through.

A mismatch is also not proof of an attack. In practice it is usually a partial download, an out-of-date page, or the wrong file. Treat it as a full stop because the cost of being wrong is a fake wallet, not because every mismatch is malicious.

## The checks that catch what a hash cannot

A matching hash proves one thing: the file you have is the file the project published. It does not prove the project's site is the real site, and it does not prove the build is free of defects.

So two further checks belong beside it:

**The domain.** Type the address or use a bookmark you made yourself. A lookalike domain publishing a file with a matching hash for its own build passes this check and fails the one that matters. [Telling the real site from a lookalike](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-vs-phishing-sites.md) covers the tells.

**The source path.** A wallet arrives from the project's own page and its release listing. It does not arrive as an email attachment, a direct message, a sponsored search result, or a "support agent" offering to help you install it.

For the wider trust question - what the wallet can and cannot protect you from - [Is OSM Wallet safe to use?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/is-osmwallet-safe.md) is the summary. For the browser extension, the equivalent of a hash check is installing from the store listing linked by the project rather than from a search result that looks similar; [Which browsers the extension runs in](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/does-osmwallet-work-in-firefox.md) covers which browsers the extension is offered in, and that answer is also a useful filter, because a listing claiming support the project does not offer is not the project's listing.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser, published as Windows, macOS and Linux builds plus a Chrome extension. Every desktop download is a single file, which is what makes this check possible at all: one file, one fingerprint, one comparison.

The wallet is actively maintained. Installer names, hashes and release notes change with each release, so the values to compare against are the ones published with the build you downloaded, not any value quoted in a guide - including this one, which deliberately quotes none.

Once the check passes, the install itself is the short part: *Downloading OSM Wallet for Windows* on Windows, *Installing the desktop app on macOS* on a Mac, *Running OSM Wallet on Linux* on Linux. The same comparison applies to every later release, which *Updating to the current release* treats as part of the update rather than as a separate habit.

### FAQ

### Do I have to check the hash every time?

Every time you install a new file, yes. It takes a minute, and it is the only check that ties the bytes on your disk to the published build.

### What if the project publishes no hash for my build?

Then that build cannot be checked this way. Ask for the value or wait for a release that publishes one; installing unverified is the thing this article exists to avoid.

### Is a hash the same as a virus scan?

No. A hash identifies a file; it says nothing about whether the software is safe or well written. It answers "is this the file the project published", and that is a different question from "is this wallet any good".

### My hash matched but the app behaves strangely. Now what?

The file is the published one, so the problem is in the app or the environment. Check the version you are running, update to the current release, and describe the behaviour with that version in hand.

### Where do I get the value to compare against?

From the project's download page or the release listing for that build, loaded yourself. Never from a message, a mirror or a screenshot someone sent you.
