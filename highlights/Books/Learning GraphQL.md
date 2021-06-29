# Learning GraphQL

## Meta Data

Source:  oreilly 
Author: None

## Highlights

### Highlights

- # 1. Welcome to GraphQL
- ## Chapter 1. Welcome to GraphQL
- The clients are more numerous today, but we’re still striving to do the
  same thing: load data somewhere as fast as possible. We need our
  applications to be performant because our users hold us to a high
  standard. They expect our apps to work well under any condition: from
  2G on feature phones to blazing-fast fiber internet on big-screen
  desktop computers. Fast apps make it easier for more people to interact
  with our content. Fast apps make our users happy. And, yes, fast apps
  make us money.
- Getting data from a server to the client quickly and predictably is the
  story of the web, past, present, and future. Although this book will often
  dig in to the past for context, we’re here to talk about modern
  solutions. We’re here to talk about the future. We’re here to talk about
  GraphQL.
- ### What Is GraphQL?
- GraphQL is a query language for your APIs. It’s
  also a runtime for fulfilling queries with your data. The GraphQL
  service is transport agnostic but is typically served over HTTP.
- A GraphQL query asks only for the data that it needs.
- This response contains
  only the data that we need.
- The query is nested, and when it is executed, can traverse related
  objects. This allows us to make one HTTP request for two types of data.
  We don’t need to make several round trips to drill down into multiple
  objects. We don’t receive additional unwanted data about those types.
  With GraphQL, our clients can obtain all of the data they need in one
  request.
- Whenever a query is executed against a GraphQL server, it is validated
  against a type system. Every GraphQL service defines types in a GraphQL
  schema. You can think of a type system as a blueprint for your API’s
  data, backed by a list of objects that you define.
- GraphQL is often referred to as a declarative data-fetching language.
  By that, we mean that developers will list their data requirements as
  what data they need without focusing on how they’re going to get it.
- ### The GraphQL Specification
- GraphQL is a specification (spec) for client-server communication. What is a
  spec? A spec describes the capabilities and characteristics of a language. We benefit from language specifications because they supply a common vocabulary and best practices for the community’s use of the language.
- If a spec and an implementation are different, what is actually in
  the spec? The spec describes the language and grammar you should use when writing queries. It also sets up a type system plus the
  execution and validation engines of that type system. Beyond that, the
  spec isn’t particularly bossy.
- ### Design Principles of GraphQL
- Even though GraphQL is not controlling about how you build your API, it
  does offer some guidelines for how to think about a service
- Hierarchical
  A GraphQL query is hierarchical. Fields are nested within other fields and the query is shaped like the data that it returns.
- Product centric
  GraphQL is driven by the data needs of the client and the language and runtime that support the client.
- Strong typing
  A GraphQL server is backed by the GraphQL type system. In the schema, each data point has a specific type against which it will be validated.
- Client-specified queries
  A GraphQL server provides the capabilities that the clients are allowed to consume.
- Introspective
  The GraphQL language is able to query the GraphQL server’s type system.
- ### Origins of GraphQL
- In 2012, Facebook decided that it needed to rebuild the application’s native
  mobile apps.
- Performance was struggling and
  the apps often crashed. At that point, engineers realized they needed to
  improve the way that data was being sent to their client applications.
- The team of Lee Byron, Nick Schrock, and Dan Schafer decided to rethink
  their data from the client side.
- In July 2015, the team released its initial GraphQL specification and
  a reference implementation of GraphQL in JavaScript called graphql.js.
- In September 2016, GraphQL left its “technical preview” stage. This
  meant that GraphQL was officially production-ready, even though it already had
  been used for years in production at Facebook.
- ### History of Data Transport
- When we think about data
  transport, we’re trying to make sense of how to pass data back and forth
  between computers. We request some data from a remote system and expect
  a response.
- Remote Procedure Call
- In the 1960s, remote procedure call (RPC) was invented. An RPC was
  initiated by the client, which sent a request message to a remote
  computer to do something. The remote computer sent a response to the
  client. These computers were different from clients and servers that we
  use today, but the flow of information was basically the same: request
  some data from the client, get a response from the server.
- Simple Object Access Protocol
- In the late 1990s, Simple Object Access Protocol (SOAP) emerged at
  Microsoft. SOAP used XML to encode a message and HTTP as a
  transport. SOAP also used a type system and introduced the concept of
  resource-oriented calls for data. SOAP offered fairly predictable
  results but caused frustration because SOAP implementations were fairly
  complicated.
- REST
- REST was defined in 2000 in Roy
  Fielding’s doctoral dissertation at University of California–Irvine.
  He described a resource-oriented architecture in which users would progress
  through web resources by performing operations such as GET, PUT, POST,
  and DELETE. The network of resources can be thought of as a virtual
  state machine, and the actions (GET, PUT, POST, DELETE) are state
  changes within the machine.
- In a RESTful architecture, routes represent information.
- REST allows us to create a data model with a variety of endpoints, a far
  simpler approach than previous architectures. It provided a new way to
  handle data on the increasingly complex web but didn’t enforce a
  specific data response format.
- The influence of REST is undeniable. It’s used to build countless APIs.
  Developers up and down the stack have benefitted from it.
- ### REST Drawbacks
- painting GraphQL as a REST killer is
  an oversimplification. A more nuanced take is that as the web has
  evolved, REST has shown signs of strain under certain conditions.
  GraphQL was built to ease the strain.
- Overfetching
- This is a huge response. The response exceeds our app’s data needs. We
  just need the information for name, mass, and height
- This is a clear case of overfetching—we’re getting a lot of data
  back that we don’t need. The client requires three data points, but
  we’re getting back an object with 16 keys and sending information over
  the network that is useless.
- We ask for
  data in a certain shape, we receive the data back in that shape. Nothing
  more, nothing less.
- Underfetching
- Our project manager just showed up at our desk and wants to add another
  feature to the Star Wars app. In addition to name, height, and mass, we
  now need to display a list of movie titles for all films that Luke
  Skywalker is in. After we request the data from https://swapi.co/api/people/1/, we still need to make additional requests for more data. This means we underfetched.
- If we wanted to list the characters that are part of this movie, we’d
  need to make a lot more requests. In this case, we’d need to hit 16 more
  routes and make 16 more roundtrips to the client. Each HTTP request uses
  client resources and overfetches data.
- Managing REST Endpoints
- Another common complaint about REST APIs is the lack of flexibility. As
  the needs on the client change, you usually have to create new
  endpoints, and those endpoints can begin to multiply quickly.
- With GraphQL, the typical architecture involves a single endpoint. The
  single endpoint can act as a gateway and orchestrate several data
  sources, but the one endpoint still makes organization of data easier.
- ### GraphQL in the Real World
- GraphQL is used by a variety of companies to power their apps, websites,
  and APIs. One of the most visible early adopters of GraphQL was GitHub.
- There are at least three conferences devoted to GraphQL specifically:
  GraphQL Summit in San Francisco, GraphQL Finland in Helsinki, and GraphQL Europe in Berlin. The community continues to grow via local meetups and a variety of software
  conferences.
- # 2. Graph Theory
- ## Chapter 2. Graph Theory
- The alarm sounds. You reach for your phone. When you turn off the
  beeping, you see two notifications. Fifteen people liked a tweet that
  you wrote last night. Nice. Three people retweeted it. Double nice. Your
  momentary Twitter notoriety was brought to you by a graph
- Graphs are all around us because they are a great way to diagram
  interconnected items, people, ideas, or pieces of data. But where did
  the concept of a graph come from? To understand this, we can take a closer look at graph theory and its origin in mathematics.
- ### Graph Theory Vocabulary
- Graph theory is the study of graphs. Graphs are used formally to
  represent a collection of interconnected objects. You can think of a
  graph as an object containing data points and their connections. In
  computer science, graphs typically describe networks of data.
- This graph diagram is made up of four circles that represent data
  points. In graph terminology, these are called nodes or vertices.
  The lines or connections between these nodes are called edges, of
  which there are five
- As an equation, a graph is G = (V, E).
  Starting from the easiest abbreviation, G stands for graph, and V describes a set of vertices or nodes.
- E stands for a set of edges. Edges are represented by pairs of nodes.
- The equation still represents the graph because there is no direction or
  hierarchy between the nodes. In graph theory, we call this an
  undirected graph. The edge definitions, or connections between data
  points, are unordered pairs.
- Let’s consider another type of graph, the directed graph
- The number of nodes is the same, but the edges look different. Instead
  of lines, they are arrows. There is a direction or flow between nodes in
  this graph. To represent it, we’d use the following
- ### History of Graph Theory
- We can trace the study of graph theory back to the town of Königsberg, Prussia in 1735. Situated on the Pregel River, the town was a shipping
  hub that had two large islands connected by seven bridges to the four
  main landmasses
- Instead of writing down every possible path, Euler decided it would be
  simpler to look at the links (bridges) between the landmasses
- He then simplified this, drawing the bridges and landmasses as what came
  to be known as a graph diagram.
- In Figure 2-12, A and B are adjacent because they are connected
  by an edge. Using these edge connections, we can calculate the degree
  for each node. The degree of a node is equal to the number of edges
  that are attached to that node. If we look at the nodes in the Bridge
  Problem, we’ll find that each of the degrees are odd
- Because each of the nodes had odd degrees, Euler found that crossing each
  bridge without recrossing was impossible. Long story short: if you take
  a bridge to get to an island, you must leave via a different bridge.
  The number of edges or bridges must be even if you don’t want to
  recross a bridge.
- The Königsberg Bridge Problem became the first theorem of graph theory.
- ### Trees are Graphs
- Let’s consider another type of graph: a tree. A tree is a graph in which
  nodes are arranged hierarchically. You know you’re looking at a tree if
  there is a root node. In other words, the root is where the tree starts,
  and then all of the other nodes are linked to the root as children.
- We can determine whether a graph is a tree based on whether it has a root node or a starting node. From the root node, a tree is connected to child nodes by edges.
  When a node is connected to a child node, that node is called a parent.
  When a child has children, that node is referred to as a branch. When a
  node has no children, it is called a leaf.
- The hierarchical structure of a tree means that trees often include
  other trees. A tree nested inside of a tree is called a subtree. An HTML
  page typically has several subtrees.
- Just as a tree is a specific type of graph, a binary tree is a specific
  type of tree. A binary tree means that each node has no more than two
  child nodes.
- When talking about binary trees, we’re often referring to
  binary search trees.3 A binary search tree is a binary tree that follows
  specific ordering rules. The ordering rules and tree structure help us
  to find the data that we need quickly.
- With the binary search tree, we can locate node 15 skillfully by
  understanding the rules of left and right. If we begin traversal at the root (9),
  we’ll say, “Is 15 greater than or less than 9?” If it’s less than, we’ll
  move to the left. If it’s greater than, we’ll move to the right.
- ### Graphs in the Real World
