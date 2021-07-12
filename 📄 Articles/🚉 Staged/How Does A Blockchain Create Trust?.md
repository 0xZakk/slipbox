---
title: How Does A Blockchain Work?
slug: how-does-a-blockchain-work
summary: ""
---

# How Does A Blockchain Create Trust?

## Introduction

This is the second article in a two-part series that seeks to answer the following questions:

1. What problem does blockchain solve?
1. How does it solve that problem?

The first article, which you can find [here](https://zkf.io/what-problem-does-blockchain-solve/), answered the first of these questions: what problem does blockchain solve.

In-short, it solves the problem of where you should place your trust as you buy, sell, and work in the global economy. The history of commerce is also the history of accounting or how we record who owns what. For exchange to happen, there has to be some mechanism that creates trust and that mechanism changes and evolves over time. That's how we got record keeping, double-entry bookkeeping, and centralized web-services. At each inflection point in the history of exchange, the old system breaks and is replaced by a new one. Blockchain solves the placement of trust issue again, but this time in the age of the internet when the volume and pace of exchange are breaking the old system.

In this article, I'd like to explain (in human terms) what a blockchain is and how it solves that placement of trust issue. You'll hear things like, "It uses cryptography" or "It's decentralized", but what do those mean and how do they make a blockchain-based system more trustworthy? That's what this article seeks to explain.

## Defining a Blockchain

In my previous article I said that, at it's core, blockchain represents n-entry bookkeeping where n is the number of participants in the system of exchange. That's a good accounting-level definition of a blockchain. A more technical way to define it is to say that a blockchain is a **distributed ledger** of **cryptographically secured transactions**, arranged in an **unbroken chain of blocks**. I'll walk through each of these pieces step by step to explain what it means and why you can trust it.

### Distributed Ledger

What does it mean that a blockchain is a distributed ledger?

In double-entry bookkeeping, two sets of books are updated simultaneously. If there is ever a discrepancy between the two books, you know an error was made. The books each constitute a ledger, recording every sale, purchase, or trade.

A blockchain is a *distributed ledger* that takes this idea of multiple bookkeepers to internet-scale. In a blockchain network, every node maintains a full copy of the ledger. When one node (i.e. digital bookkeeper) suggests a new block of transactions, every other node verifies it before adding it to their own copy of the ledger.

So why can you trust it?

One challenge of record keeping is maintaining the integrity of the records. With one bookkeeper, the entire system depends on their integrity. When you have every node verifying every update to the ledger, it becomes virtually impossible for someone to submit fake transactions.

Well with only two sets of books, it's not impossible to buy off a record keeper or otherwise manipulate the books. According to one source, Ethereum has over 11,000 nodes running the full blockchain. That means over 11,000 bookkeepers adding new blocks to the blockchain and verifying their integrity. We can trust this system because it's basically impossible for someone to submit a nefarious transaction and have it accepted. You'd have to somehow coordinate with close to 6,000 other nodes. And, given how frequently blocks are mined, you'd have only a few minutes to do so.

### Cryptographically Secured Transactions

The ledger itself is made up of blocks (think pages in an old ledger book) each of which stores a certain number of hashed transactions. What does that mean?

Hashing is a basic cryptographic function that takes some arbitrary data and secures it by generating a random fixed length string of characters, called a hash. You can't reverse a hash and the only way to reproduce a hash is with the original data. What's more, hashes are very random. Using SHA3-256 (a common hashing standard used to secure passwords) you can see how the results for `hello` and `Hello` differ:

`hello`: `3338be694f50c5f338814986cdf0686453a888b84f424d792af4b9202398f392`
`Hello`: `8ca66ee6b2fe4bb928a8e3cd2f508de4119c0895f22e011117e22cf9b13de7ef`

The only difference between these two strings is the fact that the first letter is uppercase in one and not in the other. But the resulting hashes are completely different.

Each transaction in the blockchain is stored as a hash. Then, as if that weren't enough, each transaction is hashed with another transaction to create a tree-like data structure of all the hashes in a block.

The transaction "Mark sends Ashley $50" produces a hash (`d4d1211f3caf2d44eeba05ea1316d39b9d933133d7cb068f55d583ae5db7be29`) and the transaction "Sadie sends Joseph $25" produces a hash (`f08764bf24769605b7591596d6eb4fc54a0860d7ae0ad2dd86c74cde28265a6a`). Those two hashes get hashed into a third hash (`bcd70ce218f48f6a793e7723284d63d2979a3c95a0ade72dd05b7d96f422ff9f`). This process continues until a block is mined (which I'll explain in the next phase).

The next question is of course, Why can we trust this? What about generating hashes for individual transactions or hashing transactions together makes this process trustworthy or secure?

Well let's say I try to intercept the transaction where Mark is sending Ashley $50. In my copy of the distributed ledger, instead of Ashley's account, I put in my account to receive the money. That means that the hash recording this transaction will be different on my copy of the ledger.

"Mark sends Zakk $50" hashes to `8167a2bffd5fc467d6f77995db7247ad1600f44b4c3313aa028f8e294c621e79`. That hashed with the hash of the transaction that I'm not trying to manipulate (Sadie and Joseph's) creates a different hash: `d7b5746b599b8e68903887c04f1a00d5a4fdba0989dc0d0453ba53e9ff0b8bee`. Now my copy of the ledger has a different set of transaction records from everyone else's and those differences are really obvious. So it's impossible to hide shady behavior.

When I go to submit my manipulated block to the other 11,000 Ethereum nodes, my list of transaction hashes will be completely different from all the others. Every other node in the network received the transaction "Mark sends Ashley $50" and generated the original hash above. They're going to see my transaction records, which are different, and reject them.

### Unbroken Chain of Blocks

In the distributed ledger, blocks are a group of transactions, like pages from an old ledger book. In an old, physical ledger book you could tear out a page. You could also go back and modify a page. In a blockchain, neither is possible.

In the previous section, we talked about how transactions are hashed, and then hashed together. This eventually results in the parent-most hash, called a root hash. Mining is the process of taking that parent-most hash and - you guessed it - hashing it, this time with random numbers until a hash is produced that meets some set of requirements.

So if we take our hash from above (`bcd70ce218f48f6a793e7723284d63d2979a3c95a0ade72dd05b7d96f422ff9f`) and start hashing it with random numbers (1, 2, 3, 4 ...), we'll get a new hash each time:

`1`: `fdabf3cbf9d938956563ef2b3982afad1f4d4b22b20a807e19fc55a68c3c2a04`
`2`: `8fa70988230bef2cc97730e5e7ef1c688f82cebd1388fc0dd2168d319cc844ac`
`3`: `cc6f11eb4bc378f6ccf0f9e09bf8129579009ad39991c54165a50a589cf74f67`
`4`: `6cd01bc3795e52c761d870c36ab49248c8acc948ac77617cbafa88ce9ed4a28f`

For simplicity sake, let's say our network requirements are that the new hash has to start with `cc`. Nodes on the blockchain will generate a random number and hash it with the root transaction hash until they generate a new hash that meets this requirement. When they do, they've created a new block and can submit it to the network.

In our case above, that random number is `3` and so we have a transaction hash and can mine our block. The random number is assigned to the new block and the hash will be assigned to the next block. Each block in the blockchain stores the hash of the previous block in it, which is how we form a chain of blocks.

So we have a lot more hashing - why can we trust it?

Hashing transactions with random numbers has two benefits:

First, it is now basically impossible to go back and edit a previous block. We established in the previous section that it's easy to spot when someone is trying to modify a set of transactions. Well, if someone were to try to go back and modify an existing block, not only would all the transactions be different on that block, but every subsequent block would also need to be modified somehow. So going back and trying to change history is out of the question.

Second, it's now basically impossible to remove or replace a block of transactions. Each block stores a hash of the previous block so doing so would, once again, require changing every subsequent block in the blockchain. Now, the the manipulated history creates a sequence of blocks that are different from the other copies of the ledger.

## Blockchain Trust in Action

Two final points have to be made on why we can trust blockchains and they have to do with incentives.

First, In centralized systems, like your bank, there will always be a really high incentive to try and hack in. The reward for doing so is a huge pot of money and personal data. Sure, it's all behind multiple layers of security, but it's also all there in one place. That means that centralized institutions are, and always will be, in a constant battle with hackers trying to break in.

With a blockchain, everything is decentralized. It's basically impossible to forge, manipulate, or hack a blockchain. But what's maybe just as important is that the reward for doing so is equal to the value of the transaction(s) you hack, which are generally pretty small. So there's almost no point. It'd be like someone trying to hack your credit card, not so they could max it out, but because they want the $5 you spent at Starbucks to redirect to their account instead. What's the point of that?

Second, centralized institutions have no incentive to engage in shady behavior because they would be caught. Lehman Brothers was able to lie about the state of their business by moving assets on and off their records and effectively hiding how much bad debt they held. They did that all while following the strict rules for disclosure enforced by the SEC. If those assets were all tracked on a blockchain, it would be really easy to spot how they were moving around and therefore really easy to see that the story Lehman Brothers was telling of mega-profits from novel collateralized assets was all a complete lie.

## Conclusion

Our original definition of blockchain was: a **distributed ledger** of **cryptographically secured transactions**, arranged in an **unbroken chain of blocks**. Each of these key features makes blockchain systems very secure and difficult to hack or manipulate by design.

Will everything get moved over to a blockchain? Absolutely not. In the first article, I discussed multiple different ways you can create trust in a system of exchange. You don't invite an accountant to happy hour to keep track of who owes who a drink. You just trust that everyone is keeping tabs and will settle up fairly. You effectively use the oldest form of trust in a system of exchange: direct trust in the other person. Every system of account will continue to exist in some form. But over the next decade, more and more systems will be replaced by blockchains.

## Meta Data

**Domain(s):**
- [[Building the Future]]

**Related Notes:**
- [[🟨 What is a Blockchain?]]
- [[🟨 What is a block in a blockchain?]]
- [[🟨 What problem does blockchain solve?]]
- [[🟨 How are blockchains immutable?]]
- [[🟨 What is mining and how does it work?]]