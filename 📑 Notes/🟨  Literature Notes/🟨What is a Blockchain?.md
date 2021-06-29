---
title: What is a Blockchain?
slug: what-is-a-blockchain?
type: "literature"
---

A blockchain is a **distributed ledger** of **transactions**, arranged in an **unbroken chain** of **blocks**.

*What does it mean that it's a "distributed ledger"?*

Rather than have one centralized authority maintain the ledger, every participant in the blockchain network maintains their own copy of the entire ledger (i.e. the ledger is distributed to everyone). Updates to the ledger are broadcast to every participant which then updates their own copy of the ledger, if the proposed update is valid.

*What are the transactions recorded in a blockchain?*

Transactions represent transfers of value between participants. In a cryptocurrency, this means sending some of denomination of the coin from one wallet to another. Each transaction is recorded on the blockchain in a block of transactions.

*What is a block on a blockchain?*

Transactions are committed to the blockchain in batch using a block. Each new block added to the blockchain is then linked to the previous block, creating a chain. Transactions are committed in blocks because it makes it significantly more difficult to hack or modify the ledger. It also reduces the amount of work required to commit to the blockchain.

*How are blocks chained together?*

Blocks are chained together using hashing: a function that creates a fixed-sized string out of arbitrary data. That means that the data from the previous block can be hashed with a unique number to create a fixed, computationally unique ID. This ID is then stored on the next block in the blockchain, so that each block contains this hash of the previous block. 

## Meta Data

**Source:** [[🟦Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]
