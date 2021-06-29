---
title: How Does A Blockchain Work?
slug: how-does-a-blockchain-work
summary: ""
---

# What is Blockchain

## Introduction

This is the second article in a two-part series that seeks to answer the following questions:

1. What problem does blockchain solve?
1. How does it solve that problem?

The first article, which you can find here, answered the first question above: what problem does blockchain solve.

In-short, it solves the placement of trust problem that arises in exchange and commerce. The history of commerce is also the history of accounting: how we record who owns what. For exchange to happen, there has to be some mechanism that creates trust. That's how we got record keeping, double-entry bookkeeping, and centralized web-services. At each inflection point in the history of exchange, the old system breaks and is replaced by a new one. Blockchain solves the placement of trust issue again, but this time in the age of the internet when the volume and pace of exchange are breaking the old system.

In this article, I'd like to explain (in human terms) what a blockchain is and how it solves that placement of trust issue. You'll hear things like, "it uses cryptography" or "it's decentralized", but what do those mean and how do they make a system more trustworthy? That's what I'm going to explain in this article

## Defining a Blockchain

In my previous article I said that, at it's core, blockchain represents n-entry bookkeeping where n is the number of participants in the system of exchange. That's a good accounting definition of a blockchain. A more technical way to describe it is to say that a blockchain is a **distributed ledger** of **transactions**, arranged in an **unbroken chain of blocks**. I'll walk through each of these pieces step by step to explain how it works and how it solves the placement of trust problem.

### Distributed Ledger
- What does it mean?
- How does it work?
	- Book exchange example
		- You keep an exchange of books where anyone in the group can borrow a book from anyone else
- How does this solve trust?
	- Because the ledger is distributed, it's virtually impossible to coordinate alterations to the ledger. 


### Transactions
- What does it mean?
- How does it work?
- How does this solve trust?
	- Transactions are broadcast to multiple nodes in the network, meaning it would be very difficult for a transaction to not be committed to the blockchain


### Unbroken Chain of Blocks
- What does it mean?
- How does it work?
- How does this solve trust?
	- Blocks are hashed to create a pointer from one block to the previous block
	- The hash of a block is itself a hash of every hashed transaction recorded in that block
	- That means that if someone tried to change anything about a block (i.e. by modifying a transaction, removing a transaction, or creating a non-existent transaction) the hash for that block would be different causing the entire chain of blocks to be different
	- Forcing that into the blockchain would require so much compute that it's virtually impossible


## Conclusion

Returning to our original definition of blockchain as a **distributed ledger** of **transactions**, arranged in an **unbroken chain** of **blocks**. 

Will everything get moved over to a blockchain? Absolutely not. You don't invite an accountant to happy hour to keep track of who owes who a drink. You just trust that everyone is keeping tabs and will settle up fairly. You effectively use the oldest form of trust in a system of exchange: direct trust in the other person. Every system of account will continue to exist in some form. But over the next decade, more and more systems will be replaced by blockchains. Hopefully, the shift happens before the old system breaks.


## Meta Data

**Domain(s):**
- 

**Related Notes:**
- [[🟨What is a Blockchain?]]
- [[🟨What is a block in a blockchain?]]
- [[🟨What problem does blockchain solve?]]
