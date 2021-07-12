---
title: "Track Record Tutorial"
slug: track-record-tutorial
summary: "This tutorial walks you through building a simple Ethereum Dapp to record messages to the blockchain."
---

# Track Record Tutorial

## Introduction

- Intro to Solidity
- Basics of writing smart contracts
- How to build a React app that interacts with that smart contract

## Overview

Before we get into building the application, let's talk a little bit about the tools that we're going to use here. Building an Ethereum app is a little different from building your standard full-stack app. We're not going to use a database or build an API. Instead, we're going to write smart contracts and those are going to serve as the interface to the Ethereum blockchain.

We're going to write our contracts using Solidity, the Ethereum contract language. It's a statically typed language that looks and feels a lot like JavaScript with a couple of things that feel pulled from Java. If you're familiar with JavaScript, it'll take some time for you to wrap your head around a couple of the new things that Solidity introduces. Once you're up to speed though, you'll be unstoppable.

For the front end for our application, we're going to use React with `create-react-app`. If you're currently a full-stack developer, you're probably already familiar with both of these. Interacting with a smart contract from within a React app isn't that different from interacting with an API. There are a couple of new considerations you have to account for. But overall, it's fairly straightforward.

In order to deploy our contracts and interact with them, we'll need a blockchain network running locally. This is just like when you're building an API and you launch the server for that API locally. If you've done any WordPress development, then you're familiar with setting up and running Apache or nginx locally so you can "host" Wordpress as you build out your theme or plugin. In most development now, this happens behind the scenes.

Running the Ethereum blockchain locally sounds hard - maybe it isn't, but it sounds hard - so we're going to use a tool that does it all for us. That tool is [Hardhat](https://hardhat.org/) which is actually going to be our whole dev environment. 

Finally, we need some way to connect our React front end to our Solidity smart contracts running on our local Ethereum network. There are a couple of libraries that do that. We're going to use one called [Ethers.js](https://docs.ethers.io/v5/).

## Setup

Now that we've gone over everything we're going to use in this app, let's get it all set up and ready to go.

### Getting started

To start, we're going to create a new directory called `track-record`. This is where we're going to build out the application. Once that directory is created, we'll `cd` into it and create the react application:

```sh
npx create-react-app .
```

The smart contracts are going to act as our back end or API. But instead of being an interface to our database, the contracts serve as an interface to the Ethereum blockchain.

### Setting up Hardhat

- `npx hardhat init`
- Running the node
- Creating an npm script to start the node
- Connecting a wallet to MetaMask

### Setting up Ethers.js

- Installing and including it in React
- Connecting to Metamask

## Saving a Message

### Track Record Contract

- setting up the contract
- creating the .sol file
- writing the boilerplate for the contract
- writing the first function for our contract
- compiling the contract
- deploying the contract to hardhat
- creating an npm script for deploying contracts

### Contract Front End

- Connecting to the Track Record contract
- Creating a transaction
- Signing the transaction

## Reading Messages

### Updating the Track Record Contract

- adding a function to the contract to read messages

### Contract Front End

- Invoking our contract function to get the current messages
- Displaying those messages as a list in our React Table

## Deploying to a Test Network

- Instead of a "staging" site, in crypto we use test networks
- There are a couple of test networks, we're going to deploy to **XXX** (probably robstein)
- Using environment variables for our contract addresses
- Build our react application
- Deploy our contracts to the test net
- Deploy our react application to netlify or surge
- Setting/updating the environment variables
- Testing our staging site

## Deploying to the mainnet

- Instead of a "production" environment, we use the Ethereum mainnet
- Doing this will cost you some real Eth
- Updating our environment variables
- Deploying the contract to mainnet
- Building our react app and deploying it to a production site on netlify or surge
- Testing our site in "prod"

## Meta Data

**Domain(s):**
- [[Programming]]

**Related Notes:**
- [[🟦 Beginning Ethereum Smart Contracts Programming]]
- [[🟦 Ethereum Fundamentals - Learn the Develop Smart Contracts and Enterprise DApps with Ethereum]]
- https://github.com/EmCeeEs/solidity-guestbook-example
- https://github.com/BrokenPanda/Guestbook
- https://medium.com/@james.m.kehoe/building-a-guestbook-dapp-with-vue-js-and-truffle-e0c9e3fcdeeb
