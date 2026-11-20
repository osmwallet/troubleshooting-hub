<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Issued tokens and TrustLines in practice

A TrustLine is your account's permission to hold one issuer's asset. Without it, an issued token has nowhere to land: the payment either bounces or the sender cannot complete it. Creating one also raises the XRP your account must hold, which is why trustlines are the usual reason a balance looks larger than the amount you can send.

## What a trustline actually is

XRP exists natively on the ledger. Everything else, from stablecoins to tokenised assets, is issued by an account and held by yours through a trustline: a record that says you accept that issuer's asset, up to a limit you set.

Three things follow from that. The token is only as good as the issuer. The limit is a ceiling you choose. And the trustline itself is an object on your account, which the ledger charges reserve for.

| Question | Answer |
|---|---|
| Does a trustline hold the token? | No, it records that you accept it and up to what amount |
| Can you hold a token without one? | No |
| Does the issuer control your balance? | Over its own asset, effectively yes |
| Does a trustline cost reserve? | Yes, while it exists |

A trustline is visible to anyone reading the ledger, including the limit you set and its balance. Changing a limit later is a transaction, and it costs a fee like any other.

## Creating one

Adding a trustline means naming the issuer's address and the asset's code, and choosing a limit. The wallet needs both pieces of information, and a token code alone is not enough: two issuers can use the same code for entirely different assets.

Set the limit deliberately. A limit of zero is effectively a refusal, a very large limit means you accept whatever the issuer sends, and a sensible middle value caps your exposure if the issuer's behaviour surprises you. A limit set below what you already hold blocks further incoming payments until you raise it.

## The reserve consequence

Each trustline adds to the amount your account must hold. That is why someone with several token positions can have a healthy-looking balance and almost nothing available, a situation covered in [Why the wallet shows zero available XRP](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/why-osmwallet-shows-zero-available-xrp.md).

Removing a trustline releases that reserve, but only once the token balance on it is zero. A trustline holding even a dust amount cannot be removed, which is the step that blocks most attempts to close an account, described in [Deleting an account and recovering the reserve](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-delete-account-recover-reserve.md).

## Judging an issuer

A trustline is a statement of trust, so the question is who you are trusting. The issuer can freeze the asset, change its terms, or stop honouring it, and none of that is visible in the token's code or its price chart.

The useful checks are unglamorous: has the issuer been consistent about redemption, is the address the one the project publishes, and does the token's role make sense. A token that exists only to be traded against itself is a token with no reason to hold.

## Sending and receiving tokens

To receive a token you need the trustline first; the sender cannot create it for you. To send a token, the recipient needs theirs. That asymmetry explains most failed token transfers, and it is worth understanding before the first attempt rather than after.

A trustline on the receiving account also means the recipient must hold enough reserve for it, which is why sending a token to a fresh account often fails for a reason that has nothing to do with the token.

## Removing a trustline

The order is fixed: move or spend the balance to zero, then remove the trustline, then the reserve is released. Removing one with a balance is rejected, and the message rarely says why.

This is also the cleanup that makes an account cheaper to keep, which matters if you are deciding whether to close it entirely or just simplify it.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It manages trustlines directly: adding one with an issuer address, code and limit, and removing one once its balance is empty, with the reserve effect visible in the available amount.

It is actively maintained, and the current release is downloaded from the GitHub releases page. Tokens are the responsibility of their issuers, and the wallet cannot make an issuer honest.

For the XRP side of the ledger, [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md). For importing an account with existing trustlines, *What happens to your TrustLines after an import*, and for the network you are on, *Switching between testnet and mainnet*.

### FAQ

### Do I need a trustline to hold XRP?

No. XRP is native to the ledger. Trustlines are for assets issued by another account.

### Why does a token payment fail?

Usually because one side has no trustline for it, or because the receiving account cannot cover the reserve a new trustline needs.

### Can I remove a trustline with a balance on it?

No. Move the balance to zero first, then remove it. Only then does the reserve it required become available.

### Is a trustline the same as owning the token?

No. It records that you accept the issuer's asset up to a limit. The issuer still controls the asset itself.

### Do trustlines cost anything?

They raise the XRP your account must hold while they exist. Nothing is spent, and the amount is released when the trustline is removed. An account that has collected several unused trustlines over the years can therefore hold a noticeable amount of XRP that cannot be sent until those trustlines are cleared.
