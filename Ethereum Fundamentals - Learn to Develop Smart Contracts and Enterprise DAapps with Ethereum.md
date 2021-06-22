# Ethereum Fundamentals: Learn to Develop Smart Contracts and Enterprise DApps with Ethereum

## Module 5: The Ethereum Contract Remix

[Video Link](https://learning.oreilly.com/videos/ethereum-fundamentals/0636920327905/0636920327905-video328976/)

### Module Overview

This module is about developing smart contracts
- Deploying to testnet and mainnet
- Remix environment
- Compiling and deploying code
- Testing and Debugging

### Remix Editor

Remix is one of the major dev environments for Ethereum. It's a browser-based IDE that executes in a JS environment that simulates Ethereum.

Includes a lot of reach features and comes with development Ether

https://remix.ethereum.org


## Module 6: Structure of a Smart Contract

### Module Introduction

Going to look at smart contracts, including data types, addresses, loops, custom data types, and error handling

### Base Data Types

Contracts can be written in Solidity, Vyper, JS, or other high level languages

These get compiled using the EVM and then deployed

The model is event-driven

#### `Pragma`
- Key word that invokes the compiler
- Should use greater than or equal to compiler indicator (`>=0.4.22 <0.6.0`)

#### Comments
Just like JavaScript and other C-like languages

```solidity
// This is a single line comment

/*
 * This is a mult-line
 * comment
 */
```

#### Data Types

Solidity supports the basic data types that you would expect

##### Boolean

either `true` or `false`

- ! negation
- && logical "and"
- || logical "or"
- == equality
- != inequality

```solidity
int public num2 = 0;
int public sumTotal = 0;
bool public bCond1;

function setNumbers( int _quant1, int _quant2) public {
	num1 = _quant1;
	num2 = _quant2;
}
```

```solidity
function sumIt() public returns (int _sum1) {
	sumTotal = num1 + num2;
	bCond1 = false;
	
	if (bCond1 == true) {
		return sumTotal;
	}
}
```


##### Integers

Different integer types (signed and unsigned)
- int (signed)
- uint (unsigned)
- int8
- int256
- uint8
- uint256

All the typical operators you'd expect, both math and comparison

##### Strings

Character arrays
Have to be strict with quotes
Strings cannot be compared for equivalence, but the hashes of strings can be

```solidity
function sumIt public returns (int _sum1, string memory _str1) {
	sumTotal = num1 + num2;
	
	bCond1 = true;
	_str1 = instruct;
	
	bEqual = comparesStringsbyBytes(_str, "test");
	
	if (bCond1 == true && bEqual == true) {
		return (sumTotal, instruct);
	}
}

function compareStringsbyBytes(string memory s1, string memory s2) internal pure returns (bool) {
	return keccak256(ab1.encodePacked(s1)) == keccak256(abi.encodePacked(s2));
}
```

### Address Types

We use addresses a lot in Ethereum

2 types of address:

`address`
- Meant for Etherum addresses
- Can use the same comparisons as integers

`address payable`
- same as an address but includes to special methods: transfer and send
- address payable supports sending Ether to another address

```solidity
pragma solidity 0.5.1

contract GetAddress {
	address payable public wallet1;
	
	function getMyAddress() public returns (address _addr1) {
		wallet1 = msg.sender;
		return wallet1
	}
}
```

### Data Structures

#### Enums

These are a custom data type. Given a name that contains a list of data (kind of like an array)

Enums are 0 indexed

```solidity
contract myStateContract {
	enum UserOptions {listen, connect, cancel};
	UserOptions public myOptions;
	
	constructor() public {
		myOption = UserOptions.cancel;
	}
	
	function connect() public {
		myOption = UserOptions.connect;
	}
}
```

#### Structs

Named data structure kind of like objects in other programming languages.

```solidity
struct Funder {
	address addr;
	uint amount;
}
```

#### Arrays

One data structure with multiple values. Cna be fixed size or dynamic

Values can be added with `push` and `pop`

Values are 0 indexed

```solidity
pragma solidity 0.5.1

contract ArrayContract {
	// array to keep track of several people
	Customer[] public customers;
	Tally[5] public myTally;
	int256 public custCnt = 0;
	int 256 aLength;
	
	constructor() public {
	
	}
	
	struct Customer {
		string _fname;
		string _lname;
		string _email;
	}
	
	struct Tally {
		uint m;
	}
	
	function addCustomer(string memory _fname, string memory _lname, string memor _email) public {
		customers.push(Customer(_fname, _lname, _email));
		custCnt++;
	}
	
	function removeLastCustomer() public {
		customers.pop();
		custCnt--;
	}
}
```


#### Mappings

Similar to hash tables

Add key value pairs and are able to access data by key

```solidity
contract MyPayVendorContract {
	// mapping to keep track of several vendors
	mapping(uint => Vendor) public vendors;
	mapping(address => uint) public balance;
	
	uint256 public vendCounter = 0;
	address payable public issuer;
	uint public issuerBal;
	
	event Sent(address payable from, address to, string name, uint amount);
	
	constructor() public {
		issuer = msg.sender;
	}
	
	struct Vendor {
		uint256 _cid;
		string _name;
		address payable _addr;
		uint256 _owedAmount;
	}
	
	function addVendor(string memor _name, address payable _addr, uint256 _owedAmount) public {
		vendors[vendCounter] = Vendor(vendCounter, _name, _addr, _owedAmmount);
		vendCounter++
	}
}
```

#### Event and Emit

Events are members of a contract
Events return value of arguments into the transactions log
Transaction log: Can't return or print to the console, So we write to the transaction log.
We don't return from the blockchain, just write to it

### Loops

#### For Loops
Work just like in JavaScript

```solidity
pragma solidy ^0.5.2

contract newLoopContract {
	function arith(uint a) public pure returns (uint b) {
		b = 1;
		for (uint i = 0; i < a; i++) {
			b = 2 * b + 100
		}
	}
}
```


#### While Loops

Both plain while loops and do while loops

```solidity
pragma solidity ^0.7.6;

contract WhileLoop {
	function loop() public {
		uint j;
		while (j < 10) {
			j++;
		}
	}
}
```

### Error Handling

There is no try catch in solidity, but it may get added later. You can still test for errors with commands like `require`. You can also pass a `revert`

`revert` allows us to rollback the transaction

Transactions are very role based. You're going to have more than one person involved in the smart contract. You're almost always going to have at least two roles. So when you're developing, you want to think through the roles and think through who is doing what.

#### `require`

```solidity
/**
 * Someone should only be able to send ether if they have it 
 * (i.e. you can't spend more ether than you have). We can
 * check for that using `require`.
 */
require(amount <= balance[msg.sender], "Invalid number of assets")
```

### Summary

- `pramga` and setting the compiler version
- comments and data types
- enums and structs and modeling real world data
- arrays and mappings (more complex data structures)
- events and emits
- loops
- error handling

## Module 7: Smart Contract Functions

Going to look at solidity functions

- creating functions
- passing data to function
- calling functions
- overloading
- inheritance
- modifying functions

### Function Visibility

How to think about visibility (aka scope)

Functions can take arguments as parameters and return values

Functions have to be declared with a visibility:
- `private`: only visible within the contract and can only be called by other functions within the contract (cannot be called by other contracts)
- `public`: visible to all contracts
- `internal`: only be called from within the contract
- `external`: can only be called from outside the contract (by another contract) - no way to call them internally

Examples of public v private functions:

```solidity
function get() public view returns (string memory, string memory) {
	return (value, myVal);
}

function set(string memory _value, string memory _MyVal1) public {
	value = _valule;
	myVal = _MyVal1;
}
```

Declaring and calling functions:

```solidity
// Here we have a private function
function setint (int256 i) private {
	myInt = 1;
	fullInt = myInt + 10;
}

// Here we have a public function
function set(int256 j) public {
	if (j <= 246) {
		// Here we invote the private function from within
		// the public one
		setInt(j)
	}	
}
```

### Calling and Declaring Functions

You can think of a contract as similar to an object/class in Java or C++. In order to use it in a different contract you have to instantiate it with the `new` keyword:

```solidity
// Creating an instance of a `holdData` contract and saving it
// to a variable called `hd`
holdData hd = new holdData()
```


### Function Inheritance

Smart contracts support inheritance so functions can inherit from each other (both inheritance and polymorphism)

Use the `is` keyword to inherit one contract from another:

```solidity
// We define our first contract
contract basicData {
	uint256 public keyData = 100;
	uint256 public newValue;
	
	function setVal(uint256 _iVal) public {
		newValue = _iVal;
	}
}

// Then we can inherit from that contract
contract userBase is basicData {
	holdData hd = new holdData();
	uint public theData;

	// We can add new functionality:
	function lookAtData() public view returns (uint256 _k) {
		return hd.data();
	}
	
	function getMyData(uint256 _iData, uint256 _imyData) public returns (uint256 _dataval, uint256 _key) {
		_dataval = hd.setMyData(_iData);
		
		// We can use methods in the parent contract:
		setVal(_imyData);
		theData = _dataval;
		return (theData, keyData);
	}
}
```

*It's totally cool to have two contracts in the same file. Just make sure you deploy the right contract when working with more than one contract.*

**Returning Data**

When a function returns data, we have to specify the return type in the header of the function signature. Then we can return the values using the `return` keyword. A function can return more than one data.

```solidity
function arithmetic(uint a, uint b) public pure returns (uint sum, uint product) {
	sum = a + b;
	product = a * b;
	
	return (a, b)
}
```

### Pure Functions and Modifiers

Pure functions do not update or read the transaction or block state values. Deterministic functions will always return the same value for a given set of inputs.

We use the `pure` keyword in the function header.

Pure functions can't do the following, as examples:
- access address.balance
- access state variables: `block`, `tx`, `msg`
- can only call other pure functions

#### View

View functions are a lot like pure functions. They can't modify state, emit variables, make Ether calls, etc. They can only call other functions declared as `view` or `pure`.

```solidity
pragma solidity >= 0.5.0 <0.7.0;

contract addEm {
	function myAdd(uint256 numVal, uint256 baseVal) public view returns (uint a) {
		a = numVal * baseVal + 16 + now
	}
}
```

#### Modifiers

Use modifiers to evaluate a certain condition and change the way our function executes. We add the modifier to the header.

For instance, we can limit who can run a certain function or limit it to run during a certain window of time.

Modifiers are inheritable (from a parent class)

```solidity
// Declaring a modifier:
modifier onlyAdminUser() {
	require(msg.sender == admin);
	_;
}

// Using the modifier in another function declaration:
function addUser(string memory fname, string memory lname) public onlyAdminUser {
	addUserCount();
	users[userCounter] = User(usercounter, fname, lname)
}
```

### Function Constructors

Just like the constructor function in a class. Good for initializing the contract. Can be public or private. If omitted, there is a default

```solidity
pragma solidity ^0.5.1;

contract myAddress {

	constructor (address payable wallet) public {
		myWallet = wallet
	}
	
	// ...

}
```

### Overloading Functions

We can overload functions in Solidity. Just like in Java and C++. Means that you can have multiple functions of the same name, but with different headers. The headers determine which one runs.

```solidity
// Public function that runs when someone calls addUser from
// outside the contract
function addUser(string memory fname, string memory lname) public {
	addUser();
	users[userCounter] = User(userCounter, fname, lname);
}

// Internal functions only run when called inside the contract,
// so when we call addUser in this contract we'll invoke this
// version of addUser
function addUser() internal {
	userCounter++
}
```

### Epoch Time

Ethereum uses epoch time (number of seconds since the Epoch, January 1, 1970). Can be easily converted to a more human readable time.

We get the time with `block.timestamp`

```solidity
uint256 openingTime = 1567612315;
modifier onlyWhileOpen() {
	require(block.timestamp >= openingTime);
	_;
}

function addUser(string memory fname, string memor lname) public onlyWhileOpen {
	addUser()
	users[userCounter] = User(userCounter, fname, lname)
}
```

In the above snippet of code, we declare an opening time in epoch time (in this case, Wednesday, September 4, 2019 3:51:55 PM). We also declare a modifier that will make it so our function can only be invoked after `openingTime` has passed. So with this modifier, someone can only call `addUser` once the `openingTime` has passed.

### Address Payable

A data type that can send and receive Ether

### Module Summary

- Functions
- passing and returning data
- visibility
- declaring and calling
- inheritance
- pure and view functions
- modifiers (i.e. time and ownership)
- constructors
- overloading
- payable

## Module 8: Client Side Applications

### Ganache, Node

**Ganache**
- Private ETH blockchain that runs locally
- Used for dev and testing
- Comes with ETH accounts, each of which has 100ETH
- Create a Ganache workspace

### Truffle Projects

To install truffle, run `npm install -g truffle` (version 5.0.2 used in the videos). You may need to install Python

Use `truffle init` to create a new truffle project

We can then stat writing the contract locally (VS Code with ETH plugin)

Use `truffle compile` to compile the contract

### Deploying to Ethereum

Once you've compiled the contract to Eth byte code (using `truffle compile`), you need to deploy it

The truffle starter project comes with two deployment scripts that you'll have to modify.

You want to deploy to the local network first, before deploying to a staging network

If you want to redeploy a contract, you have to run `truffle migration --reset`

This will generate some output with the contract address

### Truffle Console to Call a Contract

You can test your contract in the Truffle Console with `truffle console` in the command line. This is a CLI to the contract

You can simulate and experiment interacting with your contract

At this point, most of the Ethereum, Solidity is probably done

### Import Test Account into MetaMask

Click the account button in the top right. Then click the Import Account option

You'll need to pull the account information from Ganache, specifically the private key.

Paste the private key into MetaMask to connect to the account

### Web3.js and Building DApps

Web3 is a set of libraries for our app to work with Ethereum. You can use HTML, CSS, and JS to build apps on top of Web3.

You install Web3 with npm (`npm install web3`)

You'll need a web server to build and run your web pages so they can connect to your smart contracts. `light-server` is a good one.

