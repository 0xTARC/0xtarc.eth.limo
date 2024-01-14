---
layout: post
title: Next.js dApps Considered Harmful (Use THIS Instead)
slug: nextjs-dapps-considered-harmful-use
date_published: 2023-01-29T07:27:55.000Z
date_updated: 2023-01-29T07:27:55.000Z
tags: blog, #substack-access-everyone, #substack, #substack-type-newsletter, #Import 2023-11-08 02:56
excerpt: Next.js? More like REKT.js 😈
---

As a web3 developer for a full year, I've read a TON of open source dApp front-end code. One thing that always concerned me was the widespread usage of Next.js.

Next.js is a server side rendering (SSR) framework for React. There's a few problems with this:

## **Problems With Next.js for dApp Development**

#### **1. Next.js is too complex for nearly every dApp.**

There’s no need for the additional complexity of Next in dApps.

Do you know what Next.js consists of? It’s 38 MB, ser. I can damn near guarantee you don’t need all of that for your dApp.

#### **2. The “server” part of server side rendering is hard to decentralize.**

Server-side compute is far from a solved challenge, so most dApps just get hosted on Vercel forever.

This makes frontends built with Next the weakest link in a full-stack dApp.

> “But Taaaarc, frontends don’t really matter, users can interact with the contracts themselves, or fork the frontend and run it themselves!1!1!!

1. Knowing how to interact with smart contracts directly is hard. Have you tried buying an NFT off OpenSea with `cast` or `ethers.js`?
2. People are lazy and driven by incentives. Running a frontend is hard and expensive. No one will do it. It’s our duty to build frontends that are unstoppable by default. And open-source so *developers* can contribute to / fork them.

#### **3. Next has several features that aren’t supported by static builds.**

Just take a look at the [“Unsupported Features”](https://nextjs.org/docs/advanced-features/static-html-export#unsupported-features) section of the Next.js docs on static HTML exports.

A particularly damning subset:

- Image Optimization
- Incremental Static Regeneration
- getServerSideProps
- Headers

There are some other gotchas too that most Next users probably don’t even know about. RTFM! :3

First-class support for static builds is important because hosting a static build on a decentralized storage network like Filecoin is the best way to host a decentralized frontend.

#### **4. React lock-in.**

People who prefer Vue, for example, can feel excluded from dApp development due to the widespread usage of Next.

So anon, don’t start your next hackathon project or dApp prototype from a Next.js template.

## The Solution: Vite

> “Ok Next.js bad. Wat do Tarc?”

**Use Vite instead.**

What is Vite?

It’s a blazingly-fast build tool for JavaScript. With Vite, you get:

- a dev server with super fast hot reloads,
- hyper optimized static builds,
- AND support for several different libraries so **React**, **Vue**, *and***Svelte** maxis can *all* feel right at home.

Did I mention Vercel has first-class support for Vite? So you can still have fast & convenient preview builds through Vercel.
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2fb6ef5a8b-4600-4a3a-9fcb-8b3cbc331ea9_2762x1442.png)Vercel gmi
Sold yet? Let’s learn how to create a new React-based dApp with Vite in ONE easy command.

## **Using Wagmi’s Vite Template to Scaffold a New dApp**

Let’s use the [create-wagmi cli](https://wagmi.sh/cli/create-wagmi) to scaffold a new dApp. It’s just one simple command:

    npm init wagmi -- --template vite-react-rainbowkit

Follow the instructions from the `create-wagmi` cli to start the app. You should see something like this:
![](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F889302f3-be3b-485d-a4ff-59be5aefc274_1108x720.gif)wagmi + rainbow <3
## **Fin**

It’s important to remember that part of our jobs as software engineers is to choose the right tool for the job.

I have yet to see a case where Next.js is the right tool for building a dApp, yet it’s used EVERYWHERE in web3, even down to the dev tool documentation.

It’s time to stop. You need to be Vite-maxxing.

Thanks for reading as always and remember to subscribe for more actionable advice on Web3 frontends, UI, and UX!

[Subscribe now](#/portal/signup)

Bye bye

- 0xTARC
