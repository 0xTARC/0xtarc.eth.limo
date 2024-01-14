---
layout: post
title: Save Your dApp from Getting Rekt By Supply Chain Attacks with Lavamoat
slug: save-your-dapp-from-getting-rekt
date_published: 2023-02-04T11:32:31.000Z
date_updated: 2023-11-08T13:58:30.000Z
tags: blog, #substack-type-newsletter, #substack, #substack-access-everyone, #Import 2023-11-08 02:56
excerpt: Based @kumavis_ strikes again
---

## Another day, another package (uwu)

I found an interesting package when I was looking into the rainbowkit source: Lavamoat.

What it do?

Quoting @metamask’s [Lavamoat blog](https://metamask.io/news/security/using-lava-moat-to-solve-software-supply-chain-security/) here,

> “JavaScript is [the most popular language for developers](https://insights.stackoverflow.com/survey/2021#technology-most-popular-technologies) by far and is also very prone to supply chain attacks. This [vulnerability timeline](https://www.sonatype.com/resources/vulnerability-timeline) from 2017 shows a solid half of the attacks originating from npm…”

Basically, a simple `npm install` can rek you and your users in all sorts of ways! From an install script stealing your private keys (hope you use a separate wallet for development), to injecting hidden functionality into your app, supply chain attacks can hit from multiple angles.

Thankfully, @kumavis_ rode his terminal to the future and brought us back Lavamoat.

There are a few tools offered by LavaMoat in their [GitHub repo](https://github.com/LavaMoat/LavaMoat#how-to-secure-your-app-against-supplychain-attacks) to avoid supply chain attacks at different stages, but today I’m going to show off [@lavamoat/allow-scripts](https://www.npmjs.com/package/@lavamoat/allow-scripts) since it’s an easy starting point and prevents the most common supply chain attack vector: malicious install scripts.

And, it’s easy to use.

Here’s how:

Install the package (ironic I know, but stay with me here) with:

`yarn add -D @lavamoat/allow-scripts`

OR

`npm i -D @lavamoat/allow-scripts`

Setup, which adds a `.yarnrc` or `.npmrc` and the `@lavamoat/preinstall-always-fail` package to prevent preinstall scripts from running automatically, by doing:

`yarn allow-scripts setup`

OR

`npx --no-install allow-scripts setup`

Configure your `package.json` to run necessary scripts by running:

`yarn allow-scripts auto`

And editing the new `lavamoat` section in your `package.json`.

You can find more details and up-to-date instructions on their [npm page](https://www.npmjs.com/package/@lavamoat/allow-scripts)!

Please subscribe to stay up-to-date with the latest and greatest in web3 frontends.

[Subscribe now](#/portal/signup)

And please leave a comment / DM me on Twitter letting me know what you’d like to hear about next! Tutorials on building dApps? UI/UX critiques / refactors? Open to anything.

Thanks!

- 0xTARC
