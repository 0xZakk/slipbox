---
title: "Setting Up A Local Ethereum Dev Environment"
slug: Setting Up A Local Ethereum Dev Environment
summary: "A short and quick guide to everything you need to install and setup to start building dApps."
---

# Setting Up A Local Ethereum Dev Environment

# Introduction

- Install, set up, and explain everything you need to start developing dApps on Ethereum.

## Overview

- Node
	- build our front ends in React with Typescript
- Ganache:
	- a locally running Ethereum node that we can use for local development
	- Comes with workspaces we can use to separate our dApp environments
	- Gives us wallets with test Eth we can use
- Truffle or Hardhat
	- Need these for building our smart contracts and deploying them to our test network
	- Some differences and similarities between the two of them
- Metamask
	- Need a local wallet to actually connect to and interact with our applications

## Node

- The quick and easy way to install node is to download the package (Node and NPM) from the nodejs website
- If you wan something a little more customizable, you should use NVM for managing multiple different versions of node on the same machine
- Use nvm to install Node 14

## Truffle & Ganache

- Easiest way to install Ganache is from the website
- Install it, wait for it to unload and then create a workspace
- Install Truffle globally with NPM

## Hardhat

- Install Hardhat globally through NPM

### Hardhat v Truffle

- Both play a similar role in your stack
- there are some trade-offs between the two
- It's really just a decision around which workflow experience you prefer more

## MetaMask

- You need a wallet for interacting with your dApp
- MetaMask is a great browser-based wallet
- Install and set up
- Be sure to back up your private keys: write them down, save them somewhere you wont lose them. If you lose them and lose access to your account, there's no way to get it back

## Meta Data

**Domain(s):**
- [[Technology]]
- [[Programming]]

**Related Notes:**
- 
