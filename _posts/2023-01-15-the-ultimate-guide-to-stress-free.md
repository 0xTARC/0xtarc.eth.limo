---
layout: post
title: "The Ultimate Guide to Stress-Free, Multichain Smart Contract Calls in TypeScript: How to Build an SDK with TypeChain and Ethers"
slug: the-ultimate-guide-to-stress-free
date_published: 2023-01-15T08:58:06.000Z
date_updated: 2023-01-15T08:58:06.000Z
tags: blog, #substack, #substack-type-newsletter, #substack-access-everyone, #Import 2023-11-08 02:56
excerpt: The best, easiest, way to interact with smart contracts from TypeScript / JavaScript.
---

## The Pain of Calling Smart Contracts from the Frontend

Smart Contracts can be *real* hard to interact with, especially from JavaScript / TypeScript.

Have you ever been confused about what address a contract lives at?

[Subscribe](#/portal/signup)

Used an out of date ABI?

Wondered wtf Solidity’s `bytes32` should be in TypeScript?

Got confused context switching between Solidity and TypeScript to make sure you’re calling a function correctly?

Me too, anon.

What if we could have ONE place that keeps track of all of our addresses, ABIs, AND ALSO makes interacting with our contracts 10x easier? We can with TypeChain! Let’s see how in 5 simple(ish) steps.

## Using TypeChain and Ethers to Make Calling our Contracts 10x Easier
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2f2e25aa5a-bb8a-4a56-9f7b-2adeb5e770c9_468x600.jpg)
We can make our lives WAY easier in 5 simple steps:

1. Make sure our smart contract repo has committed up-to-date ABIs
2. Create a New TypeScript Project for the SDK
3. Add Up-to-Date Addresses to the SDK
4. Generate TypeScript code from our ABIs using TypeChain
5. Use the SDK in your dApp frontend!

If you’d like to follow along, the smart contract repo I’ll be using for this example is [hardhat-smartcontract-lottery-fcc](https://github.com/PatrickAlphaC/hardhat-smartcontract-lottery-fcc) from Patrick Collins’ excellent, free Full-Stack Web3 Development course.

#### **Step 1:****Make sure Smart Contract Repository Has Up-to-Date ABIs**

Check your smart contract repo for committed ABIs. In a default Hardhat project, it’s the `artifacts/` directory. With Foundry, the `out/` directory. Do some searching, and hopefully you’ll find those `.json` files somewhere.

If the ABIs aren’t there, compile the contracts yourself and commit the ABIs. Or ask your smart contract devs to do it (with an uwu and pwetty pwease on top).

For the `hardhat-smartcontract-lottery-fcc` repo, I did the following:

1. Forked it
2. Opened `.gitignore` and removed `artifacts/`
3. Ran `npx hardhat compile` to generate ABIs in the `/artifacts` directory
4. And committed all the artifacts to my fork.

> It’s *very* important to have up to date ABIs committed. Ideally this process happens in CI so it’s harder for them to go missing or get out of date.

#### **Step 2: Create a New TypeScript Project for the SDK**

Now that we have our ABIs tidied up and TypeChain installed, we’re done with the smart contracts. Now we just need a basic TypeScript repo. Something like [this](https://github.com/0xTARC/example-sdk/tree/12c6407) will do the trick. I recommend using that as a reference.

#### Step 3: Add Up-to-Date Addresses to the SDK

Check the docs or ask your smart contract devs where to find the addresses for the latest deployed contracts.

We’re going to put these in our SDK in a new file: `src/addresses.ts`.

Using Raffle.sol as an example:

    export const Addresses: Record<number, any> = {
      31337: {
        Raffle: '0xCf7Ed3AccA5a467e9e704C703E8D87F634fB0Fc9',
      },
      5: {
        Raffle: '0xBCAd87730Fa664ee16b6a599A3a5A94C020e1255',
      },
    }
    

So it maps the chain ID → Contract Name → Address.

Here I show two chains: `31337` is chain ID of the Hardhat network for local development, and `5` is Goerli, ‘cause I’m too poor for Mainnet. Hopefully it’s obvious how this can expand to support any number of EVM-ish chains.

> If we were really fancy, we’d use a continuous integration process to update the ABIs, deploy the contracts, save deployed addresses, and PR them to this repo on every push to main. But that’s a whole other post.

#### Step 4: Generate TypeScript code from our ABIs using TypeChain

“*Wooow* Tarc, you taught us how to commit files - *groundbreaking*. And you know what ‘CI’ means… cute. What about all that ‘making smart contract interactions easy’ stuff? I’m outta here...”
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2fce73026d-59ad-41d6-a90a-24b90cb91e3b_501x498.jpg)
Enter TypeChain.

It’s easy to use:

1. Pull your smart contract repo into your SDK repo.
2. Write some scripts to generate bindings from the committed ABIs with TypeChain.

Let’s go! We’re 80% there!

In your SDK repo, install your smart contract repo as a package with:

    npm i git@github.com:0xTARC/hardhat-smartcontract-lottery-fcc.git#bb8b04d

**IMPORTANT**: `#bb8b04d` is the latest commit hash of the smart contract repo. You want to make sure to include this when using git dependencies to avoid accidentally introducing breaking changes in your SDK.

When you’re ready for a new SDK version, you’ll re-install your smart contract repo with a new commit hash, bump the version in `package.json`, and re-release.

Now, we need to add some scripts to run `typechain` and generate code for us. Open the `package.json` of the SDK repo, go to the `scripts` section, and make it look something like this:

    "scripts": {
      "build": "rm -rf ./dist && tsc",
      "gen-hardhat-smartcontract-lottery-bindings": "find ./node_modules/hardhat-smartcontract-lottery/artifacts -name '*.json' ! -name '*dbg.json' ! -path './node_modules/hardhat-smartcontract-lottery/artifacts/build-info/*' | xargs npx typechain --target ethers-v5 --out-dir src/types",
      "prebuild": "npm run gen-hardhat-smartcontract-lottery-bindings"
    },

Finally, run `npm run build`. This will run the `prebuild` script, which runs the `gen-hardhat-smartcontract-lottery-bindings` script, which uses scary shell commands to run `typechain` on our committed ABIs from step 1.

That’s it! Your shiny new SDK is sitting in the `/dist` folder. You can use `npm link` to test locally or `npm publish` to test in prod (shoutouts Andre 🙏).
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2f40924dc9-a40b-4985-bf52-6956bb5b12c2_1512x420.jpg)Never doubt the creative forces of an autist at a shell - here’s how you can generate TypeChain bindings from a Hardhat Git repo imported as an npm dependency
> If you have a complex system of smart contracts living in multiple repos, install those repos as NPM dependencies too, add additional `scripts` to your `package.json` (e.g. `"gen-foo-bindings": "<typechain command>"`) and make sure to add those new scripts them in your `prebuild` script (e.g. `"npm run gen-hardhat-smartcontract-lottery-bindings && npm run gen-foo-bindings”`).

> You might wonder why installing a smart contract repo as an npm package is even possible, and if it would ever break. It’s admittedly a hack, and not future proof, but I it would work for 90% of cases. This is because our smart contract repo has a `package.json`, pretty much the only requirement for a Node package. This will obviously work for every Hardhat project because Hardhat is just a Node package. BUT it also works with most other projects due to the common practice of using Node packages to lint and format Solidity. For example, [PRB’s Foundry template](https://github.com/PaulRBerg/foundry-template), and [Transmissions11’s solmate](https://github.com/transmissions11/solmate). So If your smart contract repo *doesn’t* have a `package.json` and you’re against adding one, you can’t follow the rest of this tutorial word-for-word, but the principles are the same (use `curl` to download your repo instead, modify type generation command, etc). Anyways, let’s move on assuming you *can*`npm install` your smart contract repo.

#### Step 5: Using the SDK

I put together a small example repo to show how you would use this SDK’s TypeChain bindings if you were to writing some TypeScript to interact with the `Raffle` contract.

Here’s some excerpts, with some links to the full code:

- Instantiating the Contract (assuming you have a valid `signer` and/or `provider`):

    import { Addresses, Raffle__factory } from '@0xtarc/example-sdk';
    const RaffleAddress = Addresses[chainId].Raffle;
    const Raffle = Raffle__factory.connect(RaffleAddress, signer ?? provider);

- Calling `getEntranceFee` (Performing a read call):

    const entranceFee = await Raffle.getEntranceFee();

[GitHub Link](https://github.com/0xTARC/smartcontract-lottery-frontend-using-example-sdk/blob/0f575d185b990791dbe197efa5b3166cd90d80b7/src/App.tsx#L9-L25)

- Calling `enterRaffle` (Performing a write call):

    const enterRaffle = () => {
        Raffle.enterRaffle({
          value: entranceFee,
        });
      };

[GitHub Link](https://github.com/0xTARC/smartcontract-lottery-frontend-using-example-sdk/blob/0f575d185b990791dbe197efa5b3166cd90d80b7/src/App.tsx#L27-L31)

- Listening for `RaffleEnter` events and logging new entrant addresses:

    const RaffleEnter = () => {
        Raffle.on(Raffle.filters.RaffleEnter(), (entrant) => {
          console.log('New entrant: ', entrant);
        });
      };

[GitHub Link](https://github.com/0xTARC/smartcontract-lottery-frontend-using-example-sdk/blob/0f575d185b990791dbe197efa5b3166cd90d80b7/src/App.tsx#L33-L37)

You can see the full repo [here](https://github.com/0xTARC/smartcontract-lottery-frontend-using-example-sdk). `App.tsx` is probably the file you want. Play around and see how good the autocomplete is!

> This repo is based off the Rainbowkit example app `with-vite`, the best way to start a new dApp. That’s another post too - stay tuned.

### FIN

Hopefully you learned how to create a robust, flexible, envy-inducing SDK with TypeChain and Ethers! TypeChain is awesome and the more you work with it, the more you’ll like it.

Thanks for reading! Please subscribe to keep leveling up your Web3.0 crypto blockchain frontend skillz!

[Subscribe now](#/portal/signup)

Peace ✌️

- 0xTARC

### More Resources

Patrick Collins’ FREE “Full Stack Web3 Development” course doesn’t need more shills, but I’ll shill it anyway. It’s awesome for going from Blockchain Basics → Jr. Full-Stack Web3 dev. Here’s the Smart Contract Lottery portion:

[Subscribe](#/portal/signup)
