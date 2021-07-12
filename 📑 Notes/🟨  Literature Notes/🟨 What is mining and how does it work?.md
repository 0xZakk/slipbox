---
title: What is mining and how does it work?
slug: what-is-mining-and-how-does-it-work
type: "literature"
---

At a high level, mining is the process of adding blocks to the blockchain.

When a transaction is made, it is broadcast to the network of nodes. Each node receives every transaction, but not necessarily in the same order. Each mining node (i.e. nodes that perform mining calculations) keeps a list of transactions and tries to calculate a block.

To calculate a block, the mining node has to hash the contents of the block and check to see if the generated hash is valid. Valid blocks meet the difficulty criteria set by the network. A simple, naive example of a difficulty criteria is that the hash has to have 0s as the first four digits.

Mining nodes use [[🟨 What is a nonce? | nonces]] to randomly generate hashes until one of the mining nodes is able to generate a block that meets the difficulty criteria. This is why mining can be compute intensive: every mining node has to generate a random number, hash it with the contents of the block, and then test it potentially millions of times before a node generates a valid block.

When a miner creates a valid block it is added to the blockchain (ledger) and broadcast out to the network. Each mining node then verifies this block before starting the mining process all over again to find the next block.

This specific process is called [[🟨 What is Proof of Work? | proof of work]].

## Meta Data

**Source:** [[🟦 Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]