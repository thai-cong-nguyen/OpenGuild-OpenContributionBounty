---
title: How to integrate a Light Client in Decentralized Application on Polkadot Network
subtitle: Light Client - Substrate Connect provides a secure, minimalistic approach
  for Decentralized Applications on Polkadot, bypassing the need for full node installations.
author: Harry Riddle
publication: Harry’s Substack
date: October 30, 2024
---

# How to integrate a Light Client in Decentralized Application on Polkadot Network
### Introduction

Blockchain interactions require communication with a Peer-to-Peer (P2P) network to validate transactions and generate new blocks. Polkadot, like other blockchains, relies on a network of nodes that powers its consensus mechanism.

[![How to set up and run a full node on Polkadot?](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2f3cf6e7-8ec7-4622-8338-6f8d1d1ef6a8_365x250.png)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2f3cf6e7-8ec7-4622-8338-6f8d1d1ef6a8_365x250.png)Source: **[How to set up and run a full node on Polkadot?](https://www.leewayhertz.com/how-to-set-up-a-full-node-on-polkadot/)**

To communicate between the decentralized application and a network node in Polkadot is through a JSON RPC protocol. Typically, there are 2 main ways to do this:

  *  **User-Controlled Nodes:** The **Dapp (decentralized application)** connects to a node client which the users have installed and run on their machine. These nodes are extremely secure because the users fully control it, but to install and maintain them are quietly complicated as they must be active 24/7 and connect with network rapidly.

  *  **Publicly-Accessible Nodes:** There are several third-parties or platforms providing a publicly-accessible node client. These nodes are available every time when users need so they are more convenient to interact. However, their drawbacks are insecure and centralized because they are controlled by their owner.




Substrate Connect, on the other hand, is introduced for decentralized application to minimally connect to Polkadot network instead of utilizing a centralized RPC node but still securely.

### Enter Substrate Connect: A Minimalistic, Decentralized Solution

 **[Substrate Connect](https://substrate.io/substrate-connect/)** offers a secure and decentralized alternative to centralized RPC nodes. As a JavaScript library and browser extension, it enables developers to build **light clients** for Substrate chains directly in a Dapp, using **[PolkadotJS API](https://polkadot.js.org/docs/api/)** (a collection of JavaScript tools, utilities and libraries for interacting with the Polkadot network).

With Substrate Connect, there’s no need for a centralized RPC node; it operates like a bridge, running **[Smoldot](https://github.com/smol-dot/smoldot) **in the browser extension. This replaces the now-deprecated **[~~Substrate~~](https://github.com/paritytech/substrate)** and offers a robust alternative for **[Substrate](https://github.com/paritytech/substrate)** -based chains.

### Why Use Substrate Connect?

 **Polkadot** is designed with decentralization at its core, following the **Blockchain Trilemma** ( **Decentralization** , **Security** , and **Scalability** ). However, most user interfaces connect to the network through centralized nodes, making decentralization challenging. **[Substrate Connect](https://substrate.io/substrate-connect/)** provides a lightweight, decentralized option for DApps to interact securely with Polkadot, lowering complexity for end-users.

### Integrating the Light Client!

This guide walks you through integrating a Light Client with **[Smoldot](https://github.com/smol-dot/smoldot) , [Substrate Connect](https://substrate.io/substrate-connect/) **and **[Dedot](https://docs.dedot.dev/)** (an alternative to **[PolkadotJS API](https://polkadot.js.org/docs/api/)** ) in a Voting Escrow application.

Our repository is using **Next.Js** framework to build the **User-Interface** **Application** for Decentralized Application:
    
    
    https://github.com/thai-cong-nguyen/Voting-Escrow-Light-Client

* * *

> ####  **Prepare the Chain Specification JSON**

Firstly, we must prepare the chain specification json file for the Relaychain or Parachain. We can find the chain specification of our expected network in Substrate Connect repository.
    
    
    https://github.com/paritytech/substrate-connect/tree/main/packages/connect-known-chains/specs

> #### Install Dependencies

Install necessary packages such as **smoldot** , **@dedot/chaintypes** and a compatible version of **Dedot** :
    
    
    npm install smoldot dedot@0.5.0 @dedot/chaintypes

> ####  **Implement Substrate Connect Provider and Client**

Set up the **Substrate Connect Provider** and **Client** in a custom hook for use in your **Next.js** or **React** project: 
    
    
    https://github.com/thai-cong-nguyen/Voting-Escrow-Light-Client/blob/main/src/hooks/useApi.ts

[![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fad2d53e7-f2c3-4ae1-9c41-c96d987e8bba_1514x2390.png)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fad2d53e7-f2c3-4ae1-9c41-c96d987e8bba_1514x2390.png)

> #### Configure API Context for Project Layout

Integrate the Light Client provider across your application with an API Context setup:
    
    
    https://github.com/thai-cong-nguyen/Voting-Escrow-Light-Client/blob/main/src/providers/ApiProvider.tsx

[![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2f375d61-ff45-4a1d-9d80-b35dbf605ef2_1514x2876.png)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F2f375d61-ff45-4a1d-9d80-b35dbf605ef2_1514x2876.png)
    
    
    https://github.com/thai-cong-nguyen/Voting-Escrow-Light-Client/tree/main/src/app

[![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F42e11e8b-4212-4d0f-80b5-7d9b7baf210e_1514x1460.png)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F42e11e8b-4212-4d0f-80b5-7d9b7baf210e_1514x1460.png)

> #### Test the Light Client Connection

Run our application with:
    
    
    npm run dev

If successful, you’ll see confirmation in the browser console 🎉. This confirms your Light Client is now operational within your Dapp!

[![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a3718a3-c5bb-44ce-9419-5d101b2497d7_1910x314.png)](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a3718a3-c5bb-44ce-9419-5d101b2497d7_1910x314.png)

In this context, we used the **Edge Browser** to access to our application.

> #### Interact with Smart Contracts

Using the “api” client from the API Context, interact with the Relaychain or Parachain via **[Dedot SDK](https://docs.dedot.dev/)** or **[PolkadotJS API](https://polkadot.js.org/docs/api/)** to call smart contracts.

### Challenges 💪🏻

  * The **Smoldot SDK** supports **WASM-compatible** browsers, so ensure your Dapp runs on a browser optimized for WASM.




### References

  *  **[Example Staking UI Repository - Author: CocDap](https://github.com/CocDap/staking-ui)**

  *  **[Introducing Dedot: A delightful JavaScript client for Polkadot& Substrate-based blockchains](https://forum.polkadot.network/t/introducing-dedot-a-delightful-javascript-client-for-polkadot-substrate-based-blockchains/8956)**

  *  **[Polkadot Provider API: a common interface for building decentralized applications](https://forum.polkadot.network/t/polkadot-provider-api-a-common-interface-for-building-decentralized-applications/4128)**

  *  **[Smoldot updates threads](https://forum.polkadot.network/t/smoldot-updates-threads/4471)**

  *  **[smol-dot/smoldot - Lightweight client for Substrate-based chains](https://github.com/smol-dot/smoldot)**

  *  **[Introducing Substrate Connect: Browser-Based Light Clients for Connecting to Substrate Chains | Parity Technologies](https://www.parity.io/blog/introducing-substrate-connect)**




### About the Author 👋🏻

 **Bio** : _Harry Riddle, an undergraduate Web3 Developer focused on Blockchain and AI, is a member of the **OpenGuild** community in Vietnam._

 **Contact info** : 

  * **X/Twitter** : [0xHarryNguyenVN](https://x.com/0xHarryNguyenVN)

  *  **Telegram** : [@HarryRiddle](https://t.me/HarryRiddle)

  *  **Discord** : [@harrynguyen2107](http://@harrynguyen2107)



