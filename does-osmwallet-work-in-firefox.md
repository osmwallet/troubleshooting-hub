<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Which browsers the extension runs in

The extension is a Chrome extension. OSM Wallet's own site describes it as an XRPL wallet extension for Chrome, and Firefox does not appear anywhere in the site's documentation of the extension. That means Firefox is not a supported browser for it: Firefox cannot install a Chrome extension, and there is no Firefox build published to install instead.

## What the site says, and what follows

The extension page describes managing your XRP Ledger accounts "right from Chrome", and the download page lists the desktop installers for Windows, macOS and Linux alongside the extension. There is no Firefox entry, no Mozilla listing and no separate package.

That absence is decisive, because extension installation is a distribution question. A browser installs what is packaged for it and published for it; an extension that is not published for Firefox cannot be made to work by enabling a developer mode or by renaming a file.

| Browser | Engine | Runs the extension? |
|---|---|---|
| Chrome | Chromium | Yes, this is the supported target |
| Edge | Chromium | Generally yes, as it accepts Chrome extensions |
| Brave | Chromium | Generally yes, same reason |
| Firefox | Gecko | No build is published |
| Safari | WebKit | No build is published |

The Chromium rows are a compatibility consequence rather than a promise: the project documents Chrome, and other Chromium browsers share the extension format. If one of them behaves oddly, Chrome is the reference.

## Why Firefox is different rather than difficult

Firefox uses its own extension platform and its own signing requirements. A Chrome package will not load, and the browser says so plainly when you try. Supporting Firefox therefore means publishing and maintaining a second build, not adjusting a setting.

An extension runs inside the browser, so its security depends on the profile it is installed in. The desktop app does not depend on a browser profile, so clearing browser data cannot affect it. That is why the honest answer is "not supported" rather than "not yet figured out". No amount of user-side configuration crosses the gap, and a repackaged extension from an unofficial source is exactly the kind of file that carries someone else's changes into your wallet.

## What to do if you use Firefox

Use the desktop application. It is a native build for Windows, macOS and Linux, it does not depend on any browser, and it covers every operation the extension offers and more. The comparison is in [Desktop app or browser extension?](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-desktop-vs-browser-extension.md).

The practical cost is that you lose the convenience of signing inside a web page. You gain a wallet that is not loaded alongside web content, which is the trade described in the same article.

## Installing the extension correctly

Install it from the project's own extension link, not from a search result. Then check the version the browser reports against the version the download page lists, because a listing can serve an older build than the site describes, and an old build will not match the screenshots or the steps in any current guide. The comparison habit is the same one in [Which version am I running?](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/which-osmwallet-version-do-i-have.md).

If the extension refuses to load in a Chromium browser, disable other extensions first. A second wallet extension or a page-blocking tool interfering with its scripts is a common and confusing cause, and it looks like an incompatibility with the browser when it is not.

## Reading permissions before you install

The browser shows what an extension may do before it installs, and that list is worth reading rather than clicking past. An extension that signs wallet transactions needs access to the pages that talk to it; one that also asks to read every site for no stated reason is asking for more than the job requires.

Permissions can change between versions, so a list you approved a year ago is not evidence about the build in front of you.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. The desktop app covers Windows, macOS and Linux; the extension is documented for Chrome, keeps keys locally, and signs on your machine rather than on a server.

It is actively maintained, and both are distributed through the GitHub releases page. Which browsers are supported is a project decision that can change, so the site's extension page is the place to confirm rather than an article, including this one.

For first-run steps, [First run: the setup checklist](https://github.com/osmwallet/onboarding-pathway/blob/HEAD/osmwallet-first-run-setup-checklist.md); for the installer check, *Checking that your installer is the real one*; for the safety framing, *Is OSM Wallet safe to use?*.

### FAQ

### Does the extension work in Firefox?

No. The extension is built for Chrome, and no Firefox build is published. Firefox cannot install a Chrome extension, and no setting changes that.

### Which browsers are supported?

Chrome is the documented target. Other Chromium browsers such as Edge and Brave share the extension format, so they generally work, but Chrome is the reference.

### Can I side-load the Chrome extension into Firefox?

No. The formats are incompatible, and a repackaged file from an unofficial source should not be trusted with a wallet.

### What should Firefox users use instead?

The desktop app, which runs on Windows, macOS and Linux and does not depend on a browser at all. It reaches the same ledger account, so nothing has to be moved between the two surfaces.

### Why does the extension not appear in my browser's store?

Because it is published for Chrome. Check the project's extension link and the version it serves rather than searching a store for a matching name.
