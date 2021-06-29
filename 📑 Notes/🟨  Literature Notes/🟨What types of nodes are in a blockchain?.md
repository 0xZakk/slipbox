---
title: What types of nodes are in a blockchain?
slug: what-types-of-nodes-are-in-a-blockchain
type: "literature"
---

A blockchain consists of decentralized nodes, each of which maintains and verifies a copy of the ledger. Blockchains typically are made up of multiple node types:

**Full Node**

A full node is the basic node-type. Each full node contains a complete copy of the ledger and is able to verify every transaction in the ledger. When new blocks are mined, full nodes will verify their integrity before adding them to their copy of the ledger.

**Mining Node**

Mining nodes are full nodes with the additional capability that they can [[🟨What is mining and how does it work? | mine new blocks]].

**Light Node**

A light node (for instance, a wallet) maintains a reduced copy of the ledger that only includes the headers for each block and not the Merkle tree of transactions. Using a process called Simplified Payment Verification, light nodes are able to very if a transaction is in the ledger and if a block is valid.

## Meta Data

**Source:** [[🟦Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]