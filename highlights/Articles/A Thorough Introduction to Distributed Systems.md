# A Thorough Introduction to Distributed Systems

## Meta Data

Source:  https://www.freecodecamp.org/news/a-thorough-introduction-to-distributed-systems-3b91562c9b3c/ 
Author: Stanislav Kozlovski

- With the ever-growing technological expansion of the world, distributed systems are becoming more and more widespread. They are a vast and complex field of study in computer science.
- What is a distributed system?
- A distributed system in its most simplest definition is a group of computers working together as to appear as a single computer to the end-user.
  These machines have a shared state, operate concurrently and can fail independently without affecting the whole system’s uptime.
- Why distribute a system?
- Systems are always distributed by necessity. The truth of the matter is — managing distributed systems is a complex topic chock-full of pitfalls and landmines. It is a headache to deploy, maintain and debug distributed systems, so why go there at all?
- What a distributed system enables you to do is scale horizontally.
- Scaling horizontally simply means adding more computers rather than upgrading the hardware of a single one.
- It is significantly cheaper than vertical scaling after a certain threshold but that is not its main case for preference.
- The best thing about horizontal scaling is that you have no cap on how much you can scale — whenever performance degrades you simply add another machine, up to infinity potentially.
- Easy scaling is not the only benefit you get from distributed systems. Fault tolerance and low latency are also equally as important.
- Fault Tolerance — a cluster of ten machines across two data centers is inherently more fault-tolerant than a single machine. Even if one data center catches on fire, your application would still work.
- Low Latency — The time for a network packet to travel the world is physically bounded by the speed of light. For example, the shortest possible time for a request‘s round-trip time (that is, go back and forth) in a fiber-optic cable between New York to Sydney is 160ms. Distributed systems allow you to have a node in both cities, allowing traffic to hit the node that is closest to it.
- There is a way to increase read performance and that is by the so-called Master-Slave Replication strategy. Here, you create two new database servers which sync up with the main one. The catch is that you can only read from these new instances.
  Whenever you insert or modify information — you talk to the master database. It, in turn, asynchronously informs the slaves of the change and they save it as well.
- Gotcha! We immediately lost the C in our relational database’s ACID guarantees, which stands for Consistency.
- Distributed systems come with a handful of trade-offs. This particular issue is one you will have to live with if you want to adequately scale.
- Propagating the new information from the master to the slave does not happen instantaneously. There actually exists a time window in which you can fetch stale information.
- Let’s go with another technique called sharding (also called partitioning).
  With sharding you split your server into multiple smaller servers, called shards. These shards all hold different records — you create a rule as to what kind of records go into which shard. It is very important to create the rule such that the data gets spread in an uniform way.
  A possible approach to this is to define ranges according to some information about a record (e.g users with name A-D).
- We have won quite a lot right now — we can increase our write traffic N times where N is the number of shards. This practically gives us almost no limit — imagine how finely-grained we can get with this partitioning.
- We have now made queries by keys other than the partitioned key incredibly inefficient (they need to go through all of the shards). SQL JOIN queries are even worse and complex ones become practically unusable.
- Decentralized vs Distributed
- Even though the words sound similar and can be concluded to mean the same logically, their difference makes a significant technological and political impact.
- Decentralized is still distributed in the technical sense, but the whole decentralized systems is not owned by one actor. No one company can own a decentralized system, otherwise it wouldn’t be decentralized anymore.
- This means that most systems we will go over today can be thought of as distributed centralized systems — and that is what they’re made to be.
- Distributed System Categories
- Distributed Data Stores
- Distributed Data Stores are most widely used and recognized as Distributed Databases. Most distributed databases are NoSQL non-relational databases, limited to key-value semantics. They provide incredible performance and scalability at the cost of consistency or availability.
- We cannot go into discussions of distributed data stores without first introducing the CAP Theorem.
- Proven way back in 2002, the CAP theorem states that a distributed data store cannot simultaneously be consistent, available and partition tolerant.
- Consistency — What you read and write sequentially is what is expected (remember the gotcha with the database replication a few paragraphs ago?)
- Availability — the whole system does not die — every non-failing node always returns a response.
- Partition Tolerant — The system continues to function and uphold its consistency/availability guarantees in spite of network partitions
- In reality, partition tolerance must be a given for any distributed data store. As mentioned in many places, one of which this great article, you cannot have consistency and availability without partition tolerance.
  Think about it: if you have two nodes which accept information and their connection dies — how are they both going to be available and simultaneously provide you with consistency? They have no way of knowing what the other node is doing and as such have can either become offline (unavailable) or work with stale information (inconsistent).
- Such databases settle with the weakest consistency model — eventual consistency
- This model guarantees that if no new updates are made to a given item, eventually all accesses to that item will return the latest updated value.
- Those systems provide BASE properties (as opposed to traditional databases’ ACID)
  Basically Available — The system always returns a response
  Soft state — The system could change over time, even during times of no input (due to eventual consistency)
  Eventual consistency — In the absence of input, the data will spread to every node sooner or later — thus becoming consistent
- Cassandra, as mentioned above, is a distributed No-SQL database which prefers the AP properties out of the CAP, settling with eventual consistency.
- Cassandra uses consistent hashing to determine which nodes out of your cluster must manage the data you are passing in. You set a replication factor, which basically states to how many nodes you want to replicate your data.
