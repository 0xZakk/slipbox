---
title: "Building Your First DApp"
slug: building-your-first-dapp
summary: "This tutorial walks you through building a simple DApp (distributed application) using React and Hardhat."
---

# Building Your First DApp

The goal of this tutorial is to walk you through building a very simple distributed application, or DApp. We'll create a smart contract and deploy it to a local Ethereum test network before building a front end in React. If you've never done any Ethereum or smart contract development before, then this is a great place to start

## Project Setup

We're going to start by creating our React app, smart contract, and Ethereum dev environment. For our React app, we're going to use create-react-app. For our Ethereum dev environment, we're going to use a tool called [Hardhat](https://hardhat.org/) which gives us a way to run a local Ethereum node so we can deploy and test our smart contract.

We need to create our React app first, then create the Ethereum dev environment. 

To get started, create a new directory called `first-dapp` and then inside of that directory, run `npx create-react-app .` and `npx hardhat init`:

```sh
mkdir first-dapp
cd first-dapp
npx create-react-app .
npx hardhat init
```

Note the `.` with `create-react-app`! That's how we create the app in our current directory.

When Hardhat runs, you'll be prompted in the command line to select a couple of configuration options. The first question asks you to choose between creating a sample project or an empty `hardhat.config.js` file. Choose to create a sample project. Then accept the defaults for all the remaining questions by hitting the enter key.

## Project Overview

When the `init` command finishes, you'll have a folder structure that looks like this:

```sh
.
├── README.md
├── contracts
│   └── Greeter.sol
├── hardhat.config.js
├── package-lock.json
├── package.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
├── scripts
│   └── sample-script.js
├── src
│   ├── App.css
│   ├── App.js
│   ├── App.test.js
│   ├── index.css
│   ├── index.js
│   ├── logo.svg
│   ├── reportWebVitals.js
│   └── setupTests.js
└── test
    └── sample-test.js
```

A lot of this stuff is created by create-react-app. But there are some new files and folders here that were created by hardhat. Here's what each folder and file does:

- `contracts/`: This is where our solidity smart contracts will go. The sample project comes with a contract called `Greeter`, which we're going to walk through and use later on in this tutorial.
- `scripts/`: Once we have a smart contract, we need a way to deploy it to Ethereum so we can test it. The script provided in this example does just that.
- `test/`: We want to write tests for our contract so we can be sure it's working the way we intend it to. The tests we write will go in the `test/` directory. One cool thing about developing smart contracts with Solidity is that we can use Mocha, Chai, and other JavaScript tools for our tests.
- `hardhat.config.js`: Hardhat is a tool for creating and managing Ethereum dev environments. This file is where we'll configure Hardhat to do things like deploy to different test networks.

## Contract Overview

The sample project that Hardhat gives us comes with a contract called `Greeter`. It's a great "Hello World"-style example of how to write a smart contract:

```js
//SPDX-License-Identifier: Unlicense
pragma solidity ^0.8.0;

import "hardhat/console.sol";


contract Greeter {
	string greeting;

	constructor(string memory _greeting) {
		console.log("Deploying a Greeter with greeting:", _greeting);
		greeting = _greeting;
	}

	function greet() public view returns (string memory) {
		return greeting;
	}

	function setGreeting(string memory _greeting) public {
		console.log("Changing greeting from '%s' to '%s'", greeting, _greeting);
		greeting = _greeting;
	}
}
```

The first two lines are header data about our contract. The first line (`//SPDX-License-Identifier: Unlicense`) provides the license for our contract. This sample contract is unlicensed, but you'll commonly see `MIT` or `Apache-2` here. Line 2 (`pragma solidity ^0.8.0`) gives the version of Solidity our contract is written in.

Line 4 shows us how to import from another smart contract. Hardhat provides a contract called `console.sol`, which is useful for development. Solidity doesn't have something like `console.log` built in because blockchains don't have a standard out that we can print to. Hardhat provides us with something like `console.log` so we can debug our code a little more easily.

Line 7 is where our contract actually starts:

```js
contract Greeter {
	// contract code here
}
```

Contracts look and feel a lot like classes from traditional object-oriented programming. They're made up of variables for holding data and methods for accessing and modifying that data. Our sample contract has a variable declared on line 8:

```js
string greeting;
```

Solidity is a typed language, meaning you declare a variable and it's type at the same time. Here, we're creating a variable called `greeting` and setting it's type to `string`. This is where we'll save a message (i.e. "greeting") and fetch it later.

Next up in our sample smart contract, on lines 10 to 13, we have our contract's constructor method:

```js
constructor(string memory _greeting) {
	console.log("Deploying a Greeter with greeting:", _greeting);
	greeting = _greeting;
}
 ```

Constructor methods are commonly used in classes, so this will look familiar if know another object-oriented programming language. The constructor method is used to build instances of an object, in this case instances of our smart contract. It gets run when we deploy to Ethereum and "create" our contract on the blockchain.

Our construct takes a string as the parameter `_greeting`. It's common practice in Solidity to prefix function parameters with an underscore (`_`) so that they're easy to differentiate from variables. The first line of our constructor prints the parameter's value to the console using the Hardhat `console` contract we imported earlier. The second and final line of our contract assigns the value of the `_greeting` parameter to the `greeting` variable we created earlier.

We create our contract instance when we deploy it, which we do in the `scripts/sample-scripts.js` file on lines 17 and 18:

```js
const Greeter = await hre.ethers.getContractFactory("Greeter");
const greeter = await Greeter.deploy("Hello, Hardhat!");
```

Line 17 gets our contract (which we'll compile later, before running this script) and then deploys it to a locally running Ethereum node on line 18. When we deploy the contract, we pass a string into `Greeter.deploy()` which then gets assigned to the `_greeting` parameter inside our constructor.

Finally, our contract has two functions: `greet()` and `setGreeting()`:

```js
function greet() public view returns (string memory) {
	return greeting;
}

function setGreeting(string memory _greeting) public {
	console.log("Changing greeting from '%s' to '%s'", greeting, _greeting);
	greeting = _greeting;
}
```

You'll notice that these function definitions are a little different from the ones you might be used to in JavaScript. We're declaring the the parameter types (`string memory _greeting`, just like we saw in the constructor function above. But there are also a lot of keywords that come after the function name and parameter list: `public`, `view`, `returns`, etc. What are these?

The `public` keyword creates a function that can be invoked from outside the contract (i.e. it's publicly visible and callable). You can almost think of this as exposing an API endpoint for this contract: when we go to build our front end, we'll be able to call this method in the contract. If we wanted to prevent a function from being called outside the contract, we could swap `public` for `private`.

A function with the `view` keyword is one that doesn't modify the contract's state (i.e. doesn't make changes to any variable's value). `greet()` has the `view` keyword, but `setGreeting()` does not. That's because the `setGreeting()` function changes the value of the `greeting` variable.

Finally, the `greet()` method has the `returns` keyword with `(string memory)`. This is how we declare the type for the return value of our function. `setGreeting()` doesnt' have this because it doesn't return a value. `greet()` returns the current value of the `greeting` variable, which is of `string` type, so `greet()` will return a `string`.

That's a long and detailed explanation of everything that this contract does! It's not a lot of code, but there's a lot you can learn from reading it carefully.

## Compiling and Deploying the Greeter Contract

We have our contract written in Solidity. But it actually doesn't do anything for us yet. In order for us to test it out and interact with it, we have to do two things: compile it and deploy it.

Before we compile our contract, we need to tell Hardhat where we want the compiled output to go in our project. We do this in the `hardhat.config.js` file, which we'll update to look like this:

```diff
module.exports = {
	solidity: "0.8.4",
+	paths: {
+		artifacts: "./src/artifacts"
+	}
};
```

Compiling our contract is easy with Hardhat. Just run this command:

```sh
npx hardhat compile
```

The output I get, looks like this:

```sh
Downloading compiler 0.8.4
Compiling 2 files with 0.8.4
Compilation finished successfully
```

We used version 0.8.4 of Solidity because of the second line of our contract: `pragma solidity ^0.8.0;`. We compiled two contracts: `Greeter.sol` and `console.sol` (the one we imported from Hardhat).

When this finishes, you'll notice two new folders in your project: `cache/` and `artifacts/`. You can leave the `cache` directory alone. This is a folder that Hardhat uses. The `artifacts/` folder has our compiled contracts, specifically in `Greeter.json` and `console.json`.

Now that we have our compiled contracts, we can deploy them to a network. There are multiple Ethereum networks, aside from the mainnet that you're used to interacting with. Whenever you buy Ethereum or interact with a DeFi protocol, you're intereacting with mainnet. In addition to mainnet, there are multiple test networks: Ropsten, Kovan, Rinkeby and Goerli. You can think of test networks as being like staging environments. In practice, that is how they're generally used. Finally, you need a local network to develop your application with, which Hardhat gives us.

Hardhat also gives us the script we need to deploy our contracts to the local network in `scripts/sample-script.js`. The most important lines in this file are 17-20:

```js
// We get the contract to deploy
const Greeter = await hre.ethers.getContractFactory("Greeter");
const greeter = await Greeter.deploy("Hello, Hardhat!");

await greeter.deployed();
```

First we get the `Greeter` contract with `hre.ethers.getContractFactory("Greeter")`. Then we deploy the contract with `Greeter.deploy("Hello Hardhat!")`. Then we wait for it to be deployed with `greeter.deployed()`;

The best way to run this file is with the following command:

```sh
npx hardhat run scripts/sample-script.js
```

Your output should look something like this:

```sh
Deploying a Greeter with greeting: Hello, Hardhat!
Greeter deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
```

This tells us that our contract was successfully deployed, a starting value was set for our greeting inside the contract (`"Hello, Hardhat!"`), and our contract was assigned an address. Save this address! We need it later to call our contract from within our React front end.

## Building an Interface with React and Ethers.js

Our contract is compiled and deployed. Now we need to build a front end so we can actually interact with it. We're going to use React with create-react-app and a library called ethers.js for interacting with our contract.

We already created the React app, so the next thing we need to do is install ethers.js:

```sh
npm install ethers @nomiclabs/hardhat-ethers
```

Next, in `App.js`, we'll clear out the starer code provided by create-react-app and start to build out our dapp:

```js
import React, { Component } from "react";
import { ethers } from "ethers";

import GreeterContract from "./artifacts/contracts/Greeter.sol/Greeter.json";
const contractAddress = "0x5FbDB2315678afecb367f032d93F642f64180aa3";

export default class App extends Component {
	render() {
		return <h1>Hello World</h1>;
	}
}
```

We're going to use a class-based component just because it'll make organizing our code into different methods a little easier and thus a little cleaner. Aside from that, we're importing the `etheres` library as well as our contract. We're also creating a variable for our contract address.

### Reading From The Smart Contract

The first thing we want to do is read the value of `greeting` from inside our contract (it should be `"Hello Hardhat!"`). To do this, we need to:

* Check that the user has an Ethereum wallet installed in their browser
* Connect to Ethereum
* Connect to the contract
* Invoke the `greet()` method of the contract to get the value of `greeting`
* Display the greeting in the UI

Inside the `render` method of our `<App />` component, we want to check that the user has an Ethereum wallet installed. If they don't, there wont be a way for our application to connect to Ethereum. We can do that by simply adding the following:

```js
render() {
	if (window.ethereum === undefined) {
		return (
			<div>
				<h1>No Ethereum wallet found</h1>
				<p>Please install an Ethereum wallet, like MetaMask, in order to use this DApp.</p>
			</div>
		);
	}
  
	return <h1>Hello World</h1>;
}
```

Next, we need to connect to Ethereum and then our contract. We can do this inside of a `componentDidMount` method:


## Conclusion


## Meta Data

**Domain(s):**
- [[Programming]]

**Related Notes:**
- 
