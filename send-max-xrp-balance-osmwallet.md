<p align="center">
  <img src="assets/banner-article.png" alt="OSM Wallet guide" width="100%">
</p>

# Sending your full XRP balance

You cannot send the whole balance while the account keeps existing, because the account must retain its reserve. The maximum you can send is the balance minus the reserve minus the transaction fee. To move everything and keep the account, send that maximum; to move everything and end the account, delete it and sweep the balance instead.

## Why the maximum exists

The reserve is XRP the ledger requires the account to hold. A payment that would drop the balance below it is rejected before it is ever submitted, which is why a wallet can show a healthy balance and still refuse a send. The rule is not the wallet's; it is the network's, and every wallet applies it.

The fee is separate and much smaller, but it matters at the margin: the amount that leaves the account is the payment plus the fee, so a payment that exactly equals the spendable amount still fails by the fee. Leave a small margin. The fee is not fixed: it rises when the network is busy, so a margin is safer than an exact subtraction.

## The two legitimate routes

| Goal | Route | Result |
|---|---|---|
| Move the balance, keep the account | Send balance minus reserve minus fee | Account stays active, reserve stays held |
| Move the balance, end the account | Delete the account with a destination | Everything moves, reserve released, address retired |
| Move tokens as well | Send tokens first, then handle XRP | Tokens need a trustline at the destination |

The second route is the only way to move the reserve itself, and it is irreversible. Most people who ask for "send max" want the first route and would be unhappy with the second, so the distinction is worth settling before signing anything.

## Doing it in order

1. **Read the available amount**, not the balance, from the wallet.
2. **Subtract a small margin** for the fee, so the payment does not fail at the margin.
3. **Confirm the destination**, including a tag if the receiver requires one.
4. **Send the maximum**, and check the account afterwards for a small residual.
5. **Repeat if needed** once the fee has settled, since the residual is usually a fraction of an XRP.

Some wallets offer a send-maximum control that does this arithmetic for you. If yours does not, the residual after the first attempt tells you the exact shortfall, and a second, smaller send clears it.

## When trustlines change the answer

The reserve is not one number. Each trustline the account owns adds to the requirement, so an account with several can have a large balance and almost nothing available. Sending "everything" there means sending what is available and leaving the trustline reserve held, or clearing the trustlines first to release it.

The order matters: a trustline with a token balance cannot be removed until the tokens are moved, and the tokens cannot be sent to an account that has no trustline for them. That chain is covered in [Issued tokens and TrustLines in practice](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/issued-tokens-and-trustlines-in-osmwallet.md).

## What can still block the send

A destination that requires a tag and did not get one is the most common refusal that looks like a balance problem. A destination account that does not exist yet is the second: a first payment must cover the base reserve, described in [Activating an XRP Ledger account](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/activate-an-xrp-ledger-account-osmwallet.md).

If the wallet shows zero available rather than a reduced amount, the cause is different and is covered in *Why the wallet shows zero available XRP*.

## Deciding whether to delete instead

Delete when the account has served its purpose: a migration is finished, an old address is no longer used, and nobody sends to it. Keep it when the address still receives payments or when you are unsure, because the reserve is a small price for an address that works.

Deleting is irreversible and requires clearing everything the account owns first. The full procedure, including the blocking conditions, is in [Deleting an account and recovering the reserve](https://github.com/osmwallet/troubleshooting-hub/blob/HEAD/osmwallet-delete-account-recover-reserve.md).

## Where OSM Wallet fits

OSM Wallet is a non-custodial XRP Ledger wallet for desktop and browser. It displays the balance and the available amount the ledger reports, supports destination tags and memos where a receiver needs them, and supports account deletion so the reserve can be recovered when the address really is finished with.

The wallet is actively maintained, and the current release is downloaded from the GitHub releases page, which is worth checking before comparing screens with a guide.

For the arithmetic behind the limit, see *The XRP reserve, explained without the confusion*. For the fee, which is the other part of the subtraction, *What an XRP transaction actually costs*, and for a send that refuses with no explanation, *When the wallet will not send the whole balance*.

### FAQ

### Why can I not send 100 percent of my XRP?

Because the account must keep its reserve and pay the fee. The sendable amount is the balance minus the reserve minus the fee, and anything above that is rejected by the ledger.

### How do I move the reserve itself?

By deleting the account: clear trustlines and tokens, choose a destination, and the remaining XRP including the reserve is swept there. The account then stops existing.

### Why is a tiny amount left after I send the maximum?

Because the estimate and the fee rarely match exactly. The residual is normally a fraction of an XRP, and a second send clears it.

### Can I send everything to an exchange?

Only the sendable amount, and only with the tag the exchange requires. Sending without the tag can leave the deposit uncredited even though the payment succeeded.
