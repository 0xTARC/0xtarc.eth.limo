---
layout: post
title: Solidity Support in Neovim in 5 Quick & Easy Steps! (Using Coc.nvim and asdf)
slug: solidity-language-server-support
date_published: 2023-02-22T01:41:15.000Z
date_updated: 2023-02-22T01:41:15.000Z
tags: blog, #Import 2023-11-08 02:56, #substack-type-newsletter, #substack, #substack-access-everyone
excerpt: How to go to definition, see references, format, all from neovim!
---

## Neovim, solc, and coc.nvim FTW
![](__GHOST_URL__/content/images/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https-3a-2f-2fsubstack-post-media.s3.amazonaws.com-2fpublic-2fimages-2f3b9f6389-2f3f-4717-bafe-addbd9fc15c4_900x506.jpg)
Having a working knowledge of Solidity for a crypto developer in the EVM ecosystem is critical. You can be much more productive when you have the ability to dive into the source yourself. And diving into Solidity source code becomes much easier when you have deep integration in your dev environment of choice. So of course as a neck-bearded Neovim user, I wanted to share how I set this up!

## What is a Language Server?

As of Solidity 0.8.11, the Solidity team has added [LSP](https://microsoft.github.io/language-server-protocol/) support to `solc`, “which means every IDE that has Language Server support will support Solidity out of the box.”

[https://blog.soliditylang.org/2021/12/20/solidity-0.8.11-release-announcement/](https://blog.soliditylang.org/2021/12/20/solidity-0.8.11-release-announcement/)

This makes it easy for us Vim / Neovim users to get intelligent code actions (autocomplete, go to definition, batch renames, etc.) when reading and writing Solidity!

## How to Integrate the Solc language server into Neovim with coc.nvim

So here’s my guide on the *easiest, fastest* way to get Solidity support in your Vim / Neovim environment:

1. 
Let’s install solc with a version manager. I recommend asdf. Let’s install asdf by following the instructions on their [homepage](https://asdf-vm.com/guide/getting-started.html#_1-install-dependencies).

> What is asdf? asdf is a meta version manager - it gives you a common interface for installing and switching between multiple versions of multiple languages. I recommend asdf because it makes it easy to install and switch between versions of solc, node (for Typescript!), and other languages. The only language I’ve found it doesn’t play nice with is Rust. Good thing Rustaceans have rustup!

2. 
Now add the official Solidity plugin to asdf and use it install your desired version of `solc` by running:

1. 
`asdf plugin add solidity [<https://github.com/diegodorado/asdf-solidity.git>](<https://github.com/diegodorado/asdf-solidity.git>)`

2. 
`asdf install solidity 0.8.9`

3. 
`asdf global solidity 0.8.9`

1. 
You can substitute `0.8.9` for `latest`, or any other specific version of solc.

4. 
Run `solc --version` to ensure it all worked.

- 
If you want to install a specific version of solc, say 0.8.12, you can do `asdf install solidity 0.8.12` to install, and `asdf global solidity 0.8.17` to make it available in your path

3. 
Now install [Coc.nvim](https://github.com/neoclide/coc.nvim) by following the instructions in their README. This will allow us see LSP suggestions and run LSP actions in Vim.

- 
What is Coc? The Coc.nvim plugin stands up a Node process to host VSCode extensions, allowing you to use VSCode plugins in your Vim environment! And it works in both Vim *and* Neovim - don’t be fooled by the name.

4. 
Now install the coc-solidity plugin to get the Language Server actions into Vim by opening Vim / Neovim and running:

1. 
`:CocInstall coc-solidity`

5. 
All done! Try it out by opening a `.sol` file, going to a variable usage, and trying the “go to definition” action. If you followed the Coc.nvim [example configuration](https://github.com/neoclide/coc.nvim#example-vim-configuration), you can do this with `gd` in normal mode.

That was 5 easy steps to get Solidity LSP support in Vim and/or Neovim. Have fun, and please reach out on Twitter if you have questions or suggestions for future posts [@0xTARC](https://twitter.com/0xTARC).

[Subscribe](#/portal/signup)

Bye for now,

- Tarc

[Subscribe](#/portal/signup)
