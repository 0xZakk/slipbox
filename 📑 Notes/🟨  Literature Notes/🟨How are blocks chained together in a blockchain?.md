---
title: How are blocks chained together in a blockchain?
slug: how-are-blocks-chained-together-in-a-blockchain
type: "literature"
---

Blocks in a blockchain are chained together using [[🟨What is a Hash function? | hashes]], special functions that produce unique strings of data based on an input. The contents of each block and unique number are hashed together to create a unique string. This unique string, or hash, is added to the next box as a cryptographically verifiable way of pointing back to the previous block.

This hashing process ensures the integrity of the chain and the individual blocks at the same time.If a block or any of the transactions inside of it are modified, it produces a different hash. That invalidates that block and the next blocks link back to it.

This is one of the things that makes blockchains incredible secure. If someone wanted to modify the ledger, the would have to modify a transaction and all subsequent blocks in the blockchain. Because this would be so computationally expensive, we can say that blockchains are effectively immutable.

## Meta Data

**Source:** [[🟦Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]