---
title: How are blockchains immutable?
slug: how-are-blockchains-immutable
type: "literature"
---

Blockchains are *effectively immutable*, meaning it is possible to change the ledger, but it's so difficult and compute intensive that we can effectively consider the ledger immutable.

This effective immutability is ensured through [[🟨 What is a Hash function? | hashing]] - a way of taking data of arbitrary size and producing data of fixed size, called a hash. Each block is chained to the previous block through a hash of the previous block and it's transactions

So if one of the transactions in a block is changed, the transaction would produce a different hash, which would cause the block to produce a different hash. Every subsequent block in the chain would then have to be changed, which would require an enormous amount of computational power. 

## Meta Data

**Source:** [[🟦 Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]