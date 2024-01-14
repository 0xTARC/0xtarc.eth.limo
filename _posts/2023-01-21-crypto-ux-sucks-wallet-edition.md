---
layout: post
title: "Crypto UX Sucks: Wallet Edition"
slug: crypto-ux-sucks-wallet-edition
date_published: 2023-01-22T06:47:00.000Z
date_updated: 2023-01-22T06:47:00.000Z
tags: blog, #substack, #substack-type-newsletter, #substack-access-everyone, #Import 2023-11-08 02:56
excerpt: Zooming in on a specific aspect of crypto UX that SUCKS, explaining WHY it sucks, and sharing some tools and ideas to fix it.
---

## Crypto Wallet UX Sucks
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2fbd41e62b-4cf0-41fe-8010-875b48d24c21_600x893.jpg)
It’s no mystery that interacting with blockchains is still hard compared to the buttery-slickness of today’s FinTech.

Think about the difference between buying Minecraft on the App Store with PayPal, and buying an NFT on OpenSea with MetaMask.

[Subscribe](#/portal/signup)

This is the gap we need to fill.

And the novice users aren’t the only ones struggling.

Even “crypto natives” struggle with things like

- sending and receiving payments
- accidentally signing malicious transactions
- managing multiple accounts
- doing multi-sig transactions in a timely manner
- needing like 27 clicks to do a simple swap
- losing keys
- AND MORE! WTF!

We can do better 🙂

But how? First, let’s define what a wallet is. In UX-speak, what are the “affordances” of a wallet?

When I say “wallet” I’m not thinking about a hunk of metal engraved with 24 magic words. I’m thinking along the lines of MetaMask or Coinbase Wallet - something you would use every day for financial transactions. In general, this wallet should let you do the following:

- Generate, securely store, and backup private keys
- Manage multiple accounts (e.g. a “checking account” and an “investment account”)
- Share your accounts with others
- Allow you to create, cancel, and see past transactions, like sending money to a friend.

Most people use Trust Wallet or MetaMask for these abilities.

Some use hardware wallets like Ledgers, which can add even *more* complexity (worth it!).

And multi-sigs signers? Forget it. Advanced users only, and we quadruple check every step of the way.

## Tools and Ideas to Make it Better

It can be so much better. Here are some tools and ideas to improve wallet UX:

#### Tools

- 
Gnosis Safe Modules. [Zodiac](https://github.com/gnosis/zodiac) has a ton of great ones.

- 
Zodiac, “The expansion pack for DAOs”, provides amazing extensions for your multi-sig wallets like Gnosis Safe. They provide **Modules**, like **[Exit](https://github.com/gnosis/zodiac-module-exit)** for DAOs built on Gnosis Safe to allow their members to “rage quit”, or [Reality](https://github.com/gnosis/zodiac-module-reality) to do things like execute on-chain transactions based on the results of a Snapshot vote. There’s also **Modifiers**, which includes [Roles](https://github.com/gnosis/zodiac-modifier-roles) for roles-based access control and [Delay](https://github.com/gnosis/zodiac-modifier-delay) for time-delayed contract execution, and **Guards**, like [Scope](https://github.com/gnosis/zodiac-guard-scope) for whitelisting specific contract interactions.

- 
[delegate.cash](https://delegate.cash/), allows for safe delegation of certain transactions involving cold wallet assets from a hot wallet.

- 
[MetaMask Flask](https://metamask.io/flask/) and [Snaps](https://metamask.io/snaps/).

- 
MetaMask Flask is the “canary” build of MetaMask for developers that lets you install Snaps. Snaps are a really exciting feature that let you build and install extensions for MetaMask. Some of my favorite snaps:

- 
[Snap auto approvals](https://github.com/livingrockrises/snap-auto-approvals)

- 
Creates a “session” where transactions get auto-signed until the session ends. Similar to how you can sign into a bank account, do multiple transactions, then sign out. This is *amazing* for blockchain gaming.

- 
Multi-Chain snaps, allowing you to interact with non-EVM blockchains through MetaMask.

- 
[BTCSnap](https://github.com/KeystoneHQ/btcsnap), [FilSnap](https://github.com/ChainSafe/filsnap), [ArSnap](https://github.com/pianity/arsnap), [metamask-snap-polkadot](https://github.com/ChainSafe/metamask-snap-polkadot) , etc.

- 
[Coinbase Wallet](https://www.coinbase.com/wallet)

- 
The free human-readable usernames make sending and receiving money between friends a breeze. We shouldn’t need to keep a list of our friends’ public keys. An integrated fiat on-ramp too? Nice. I recommend this one, paired with a Trezor or Ledger, to people new to crypto.

#### Some Ideas

Please build this!

- Integrate the [GasHawk](https://gashawk.io/) API into a MetaMask snap, giving you the option to schedule a transaction to be executed at a time with low gas. No extra RPC needed.
- Don’t like that MetaMask now tracks your IP? Build an “AdBlock” snap (lol).
- Snap that integrates with EPNS so you get alerted in MetaMask for things like a low health factor, or a friend requesting payment.
- A snap for DefiLlama’s meta-dex aggregator. Always use the superior swap, anon.
- This one is obvious but I can’t help mentioning it: how about a “Snap Store”? This is how Snaps are currently distributed

![Untitled](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack.com-2fimg-2fmissing-image.png)
Clunky? Well the Snap Store aggregates all Snaps, with ratings. You can even integrate payments, allowing developers to monetize MetaMask plugins.

- A point-of-sale / on-ramp built on the [Gas Station Network](https://opengsn.org/), allowing anyone with a credit card (no gas in their wallet needed) to settle transactions on crypto rails.
- A Gnosis Safe Module for small investment clubs/farming as a service providers.
- A Gnosis Safe Module for functionality like GasHawk’s, e.g. delaying a transaction until a time where the gas price is expected to be low.
- ENS integrations like Coinbase Wallet has everywhere please.

Hopefully you learned something, anon! Thanks for reading and subscribe for more actionable advice on Crypto UI, UX, and frontend development.

[Subscribe](#/portal/signup)

Peace :3

- 0xTARC

#### Additional Resources:

DeveloperDao’s MetaMask Snap tutorial
