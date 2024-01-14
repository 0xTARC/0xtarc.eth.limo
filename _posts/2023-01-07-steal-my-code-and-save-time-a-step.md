---
layout: post
title: "Steal my Code & Save Time: A Step-by-Step Guide to Building a Buttery Smooth, Composable, Health Factor Slider"
slug: steal-my-code-and-save-time-a-step
date_published: 2023-01-08T01:32:11.000Z
date_updated: 2024-01-15T01:42:55.000Z
tags: blog, #substack-type-newsletter, #substack, #Import 2023-11-08 02:56, #substack-access-everyone
excerpt: Beautiful, robust, design system-worthy slider built with Typescript, React, Radix UI, and Stitches. Perfect for controlling Health Factors and Collateralization Ratios in dApps.
categories:
- react
- radix-ui
author:
- Bart Simpson
- Nelson Mandela Muntz
meta: "Springfield"
---

## The Problem

So you need your users to choose from a range of values while giving them a hint about how risky their choice is.

Maybe you reach for Material UI, install 6MB of potentially dangerous dependencies for a single, hard to customize component.

Maybe you're bought-in to the headless component wave and are in the middle of migrating to your own design system (my case!).

Or maybe you just want a great slider with minimal dependencies.

No matter your situation, this one's for you, anon.

## The Code

So, here's the Slider. It’s based on a Slider I built for the canonical FIAT protocol frontend.

It’s built with Typescript, React, and Radix UI. The Slider is styled with Stitches, though with a little effort you can swap for CSS Modules or another styling solution.
![](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6609b3f8-b240-4a44-926e-8fa1210c2fee_1618x938.gif)
[Edit on CodeSandbox](https://codesandbox.io/s/github/0xTARC/HealthFactorSlider/tree/main/)

Details of note:

- The Slider’s track is white by default. The gradient is implemented as a `color` variant with Stitches. Variants are a powerful way to express a lot of style without a lot of code. Plus, a ton of devs are used to using variants thanks to MUI (`color='primary’`, anybody?). If you're interested, read more on variants [here](https://ped.ro/writing/variant-driven-components).
- A [custom data attribute](https://github.com/0xTARC/HealthFactorSlider/blob/main/src/Slider/Slider.tsx#L124), `[data-inverted]`, is added to SliderRoot. This is then used as a [selector](https://github.com/0xTARC/HealthFactorSlider/blob/main/src/Slider/Slider.tsx#L41) to reverse the gradient. This is in line with the intuitive Radix component APIs, and makes it easy to port the styling of this component over to CSS Modules, or another styling solution. (CSS Modules ftw, I just happened to have Stitches installed because we're migrating off Next UI.)
- Fully typed so devs will know all valid color values without having to read the source.

[![Slider color prop autocompletion](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_lossy/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb4d4231d-7dd7-4b82-80d2-a9dfbe312d8f_1012x760.gif)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fb4d4231d-7dd7-4b82-80d2-a9dfbe312d8f_1012x760.gif)Good types = good autocompletion = happy devs
Had to do some Typescript-fu to get that to work, just look at how wonky the [SliderProps interface](https://github.com/0xTARC/HealthFactorSlider/blob/main/src/Slider/Slider.tsx#L75-L89) is. But from my experience with design systems, wonky types are often the case when creating components that will have good autocompletion for devs.

Tried for a few mins to replicate that *choice* Developer eXperience™️ with `vanilla-extract` but couldn't quite get it. If you can, please message me and I'll add that example to the CodeSandbox & repo.

Thanks for reading! :3

- 0xTARC

[Subscribe now](#/portal/signup)
