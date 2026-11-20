<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Buying XRP inside the wallet

Where the wallet offers a buy route, it hands the purchase to a third-party provider: you are buying from that company, at their price, under their terms. The wallet is a doorway, not the seller. That single fact explains the fees, the identity checks and the reason the amount that arrives is smaller than the amount quoted elsewhere.

## Who you are actually buying from

A non-custodial wallet does not hold your money and cannot sell you an asset. To turn a card payment into XRP it needs a counterparty licensed to take the card, and that counterparty sets the rate, the spread, the processing charge and the minimum.

| Question | Answer |
|---|---|
| Who sets the price? | The provider, not the wallet |
| Who charges the card fee? | The provider and the card network |
| Who asks for identity documents? | The provider, as its own obligation |
| Where does the XRP arrive? | Directly into your wallet address |
| Can the wallet refund a purchase? | No, it was never the seller |

The last row matters more than it looks: a dispute about a purchase goes to the provider's support, not to the wallet's, because the wallet has no record of the transaction beyond the XRP that arrived.

## Why the price looks worse than the chart

Three costs stack up, and only one of them is visible as a "fee".

**The spread.** The provider quotes a rate slightly worse than the market, and that difference is where much of the margin sits. It is not labelled a fee, because it is not one.

**The processing charge.** A card payment costs a percentage, and small purchases pay a fixed minimum that can swallow a large share of the amount.

**The network cost.** Moving the XRP to your address costs the ledger fee, which is small but real, described in [What an XRP transaction actually costs](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-fees-when-sending-from-osmwallet.md).

Comparing a provider's quote with a spot chart is therefore misleading. The honest comparison is the total you pay against the amount that lands.

## When buying inside the wallet makes sense

It is convenient and fast: no second account, no withdrawal step, and the XRP goes straight to the address you control. For a first small purchase, or for topping up to clear a reserve, that is a reasonable trade.

It stops making sense as the amount grows. Spreads and card fees scale with the purchase, while an exchange's fee does not scale the same way, so the gap widens. Anyone buying regularly will find the in-wallet route the more expensive of the two.

## When an exchange is cheaper

If you are buying a meaningful amount, or buying regularly, the exchange route usually wins: better rate, lower percentage, and a withdrawal you control. The cost is an extra step and the discipline of withdrawing rather than leaving the balance there.

That discipline is the whole point. XRP left on an exchange is not self-custody, whatever the app icon suggests, and [What a non-custodial wallet actually means](https://github.com/osmwallet/beginner-explainers/blob/HEAD/non-custodial-wallet-meaning-osmwallet.md) explains why the difference matters. The withdrawal path is in *Moving XRP from an exchange into your own wallet*.

## The identity step

Providers collect identity documents because they are required to, not because the wallet asked. That means a purchase leaves a record with a company you have just started a relationship with, which is a different privacy position from buying peer to peer.

If that is unacceptable, the in-wallet route is not the one to use, and no setting changes it.

## Deposits, minimums, and the first purchase

A first purchase often lands at a size that makes the account barely usable: enough to exist, not enough to send. That is the reserve doing its job, covered in [The XRP reserve, explained without the confusion](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/xrp-reserve-explained-osmwallet.md).

Check the minimum before buying small. A minimum above your intended amount is a common surprise, and promising-looking quotes sometimes exclude the card charge until the final screen. A quote is also time-limited, so a slow checkout can land a different amount than the one previewed.

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. Where a build includes a purchase route, it connects you to a provider and receives the XRP at your own address, so the asset lands in a wallet whose keys you hold rather than in custody.

It is actively maintained, and the current release is downloaded from the GitHub releases page; the presence and wording of any purchase option is a build-level detail, so check the app rather than a screenshot.

For what happens after the XRP arrives, *Sending your full XRP balance* and *Is OSM Wallet safe to use?*.

### FAQ

### Does the wallet charge a fee for buying XRP?

The wallet is not the seller, so the costs come from the provider: a spread, a card processing charge and a minimum. The wallet takes no cut of the purchase.

### Why is the amount I received smaller than the quote?

Because the quote typically excludes the processing charge and reflects the provider's rate rather than the market's. Compare the total paid with the amount that landed.

### Do I have to provide ID?

The provider does, as a legal obligation. It is their requirement, not the wallet's, and it cannot be waived in settings.

### Is buying in the wallet cheaper than an exchange?

For small, occasional purchases it can be simpler and close enough. For larger or regular buying, an exchange plus a withdrawal is usually cheaper.

### Can I cancel a purchase?

Only through the provider, under their terms. The wallet has no role in the sale and cannot reverse it.
