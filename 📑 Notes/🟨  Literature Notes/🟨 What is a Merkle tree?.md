---
title: What is a Merkle tree?
slug: what-is-a-merkle-tree
type: "literature"
---

A Merkle tree data structure is a tree structure in which each node is a hash of it's child nodes, except the leaf nodes which are a hash of a transaction.

So every transaction is added to the tree as a leaf. The hash of that transaction is then stored as the transaction node's parent (`Ta`). The parent of the hash node `Ta` is hashed together with it's sibling hash (`Tb`) to create a new hash `Tab`, which is then hashed with it's sibling (`Tcd`) to create a parent node `Tabcd`. This continues up the tree until the root: a hash of every hash of hashes of hashes, etc.

The final hash is known as the Merkle root and is stored in the header of a block on the blockchain. 

## Meta Data

**Source:** [[🟦 Beginning Ethereum Smart Contracts Programming]]
**Domain(s):**
- [[Technology]]