---
title: "concat: Learn JavaScript's Array Methods by Building Them"
slug: concat-learn-javascripts-array-methods-by-building-them
date_published: 2020-12-17T00:00:00.000Z
date_updated: 2021-04-08T12:44:41.000Z
tags: Programming, JavaScript
excerpt: For the third article in the series, we explore the concat method and how we can abstract complicated logic into a function so we don't have to think about it.
---

Arrays are one of JavaScript’s most robust features. Their flexibility and power are subtle, so the spotlight tends to get shined on functions or objects instead. This results in mangled coding-through-hoops for even some of the simplest tasks involving an array.

We have now explored two popular JavaScript array methods and seen how they can make our code easier to read. In this article, we’ll continue by exploring the `concat` method, which provides an easy way of joining multiple arrays into one.

## How it Works

The `concat` method (short for *concatenate*) takes any number of arrays and combines them into one, new array. We can do this without the `concat` method. For instance, if we had the following two arrays:

    const num1 = [1, 2, 3];
    const num2 = [4, 5, 6];

We could combine them with two `for` loops (one per array):

    const nums = []
    
    for (let i = 0; i < num1.length; i++) {
      nums.push(num1[i])
    }
    
    for (let i = 0; i < num2.length; i++) {
      nums.push(num2[i])
    }
    
    console.log(nums) // [1, 2, 3, 4, 5, 6]

This solution works just fine, but it has a couple of drawbacks.

Namely, it’s not very dynamic. What do we do if we need to add a third array? Do we add a third loop? Well, let’s make it more dynamic:

    const numArrays = [num1, num2]
    
    const nums = []
    
    for (let i = 0; i < numArrays.length; i++) {
      let currentArray = numArrays[i]
      for (let j = 0; j < currentArray.length; j++) {
        nums.push(currentArray[j])
      }
    }
    
    console.log(nums) // [1, 2, 3, 4, 5, 6]

In the above block of code, we’re taking the two arrays, `num1` and `num2` and adding them to an array, `numArrays`. This will let us handle all of our arrays together. We then loop through our list of arrays. We can then loop through each array and push the items into our `num` array.

It’s more dynamic, meaning we can more easily accommodate changes in our data. There’s also a point to be made about nested loops, but we can leave that aside for now. The main issues are that this block of code is long, difficult to read, and hard to understand what we’re doing. If you saw this block of code without any comments, it would take you some time to understand what the developer was trying to do.

We want to do something like this:

    const num1 = [1, 2, 3];
    const num2 = [4, 5, 6];
    
    const nums = num1.concat(num2)
    
    console.log(nums) // [1, 2, 3, 4, 5, 6]

Blink and you’ll miss it! This block of code achieves the same result in one, easy to read line.

Hallelujah!

## Implementing Our Own

We’ve established what it does so let’s talk about how `concat` does it. To implement our own, we need a function that:

- Takes any number of arrays
- Loops through them all
- Adds the items of each array into a final array
- Then, returns that final array

That is the specification of the final version of `concat` that we’ll build, but to get their we’re going to practice a trick called *reduction*. Rather than try to solve for all of that, we’re going to reduce the complexity of the problem a bit. Our first solution will take two arrays and concatenate them, then we’ll modify that solution to handle any number of arrays.

So to start we need a function that takes two arrays:

    function concat(arr1, arr2) {
    	// More to come here ...
    }

Let’s combine these two arrays into a single array, so we can handle them together. Then we can loop through the combined array:

    function concat(arr1, arr2) {
      let arrs = [arr1, arr2]
      
      for (let i = 0; i < arrs.length; i++) {
        // More to come here ...
      }
    }

The next step is to then loop through the two passed in arrays and push each item into a `final` array that we can then return:

    function concat(arr1, arr2) {
      let arrs = [arr1, arr2]
      let final = []
      
      for (let i = 0; i < arrs.length; i++) {
        let currentArray = arrs[i]
        for (let j = 0; j < currentArray.length; j++) {
          final.push(currentArray[j])
        }
      }
      
      return final
    }

This is the same as our implementation from before, but we’ve pulled out the difficult to read logic and made it reusable. Now, when we want to concatenate two arrays, we don’t have to think of *how* to do it, just that we want to:

    const letters1 = ['a', 'b', 'c'];
    const letters2 = ['d', 'e', 'f'];
    
    const letters = concat(letters1, letters2);
    
    console.log(nums) // ['a', 'b', 'c', 'd', 'e', 'f']

We’ve solved our reduced version of the problem. We have defined a function that takes two arrays and concatenates them into a new array. Now we need to solve the original scope and make it so this function will work with any number of passed in arrays. For that, we need a dynamic way of handling the function’s passed in arguments.

### Using a Function’s `arguments`

We need a way of handling any number of passed in arrays. There are a couple of ways we can do this, but the simplest is to use the built-in `arguments` object:

    function printArguments() {
      // Print out the `arguments` object
      console.log(arguments)
    }
    
    printArguments('hello', 'world')

In the above snippet, we’ve defined a function that uses `console.log` to print the `arguments` object. We then invoke this function passing in two arguments: `'hello'` and `'world'`.

If you run this code, you’ll see something like this in the console:

    {
      '0': 'hello',
      '1': 'world',
      length: 2,
      callee: ƒ printArguments(),
      __proto__: { ... }
    }

The `arguments` object is array-like. You can access items in `arguments` by index (i.e. `arguments[0]` will give you `'hello'`) and it has a length, but it isn’t a true array.

But, if we can access items by index, then we can loop through it. So we can modify our implementation of `concat` to use `arguments`:

    function concat() {
      let final = []
      
      for (let i = 0; i < arguments.length; i++) {
        let currentArray = arguments[i]
        for (let j = 0; j < currentArray.length; j++) {
          final.push(currentArray[j])
        }
      }
      
      return final
    }

We’ve replaced the `numsArray` with `arguments`, but otherwise this block of code is the same as the one before it. And now our `concat` method can take any number of arrays passed in:

    let num1 = [1, 2, 3]
    let num2 = [4, 5, 6]
    let num3 = [7, 8, 9]
    let num4 = [0]
    
    let nums = concat(num1, num2, num3, num4)
    
    console.log(nums) // [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]

We’ve finished our version of `concat`, but we could certainly make it a little cleaner, which we’ll do now.

## Cleaning Up Our Implementation

Our implementation of `concat` works great, but it’s not very clean. In previous articles, I talked about how loops in general are difficult to read. Well, nested loops are especially difficult!

We can start to clean this up by replacing our `for` loops with `forEach`. We simply have to convert `arguments` to a full array:

    function concat() {
      let final = []
      let args = Array.from(arguments);
    
      args.forEach(arg => {
        arg.forEach(num => final.push(num))
      })
    
      return final
    }

We’ve shaved off a few lines of code and we’ve made our implementation easier to read through. We can take this one step farther but using the rest and spread operators.

First, we’ll implement the rest operator, which is a way of replacing `arguments`:

    function concat(...args) {
      let final = []
    
      args.forEach(arg => {
        final = [ ...final, ...arg ]
      })
    
      return final
    }

That shaved off a few lines. This is also the more modern way of handling the problem of an unknown number of inputs.

Next, we’ll use the spread operator to remove on of our loops:

    function concat(...args) {
      let final = []
    
      args.forEach(arg => {
        final = [ ...final, ...arg ]
      })
    
      return final
    }

The spread operator “unpacks” an object, like an array. I liken it to holding a backpack upside down over a suitcase and unzipping it: everything in the backpack is going to fall out into the suitcase.

Here, we’re unzipping each passed in array (`arg`) and letting everything fall into the `final` array.

Why do we do the same with `final`? Well, with each iteration of the loop, we’re creating a new array that replaces the previous version. So after the first iteration of our `forEach` loop, the `final` array would hold all of the items in the first array passed into `concat`. We want these items inside of the current version of `final` to be in the next version (after the next iteration of `forEach`), so we unzip it too.

## Conclusion

You can still see that any Array method can be implemented with a loop, but our implementation of `concat` was a little more complex than our previous implementations of `forEach` and `map`. We’re able to see that these array methods are not just about making our code more declarative, they’re also about hiding complexity. This will be even more true as we explore some of the more complex Array methods, like `reduce`.

I'm going to go through and explain and implement every built-in Array method, which will help you understand how they work as well as when and how to use them. To follow along, sign up for my [newsletter](https://hawthorne.substack.com/) and follow me on [Twitter](https://twitter.com/ZFleischmann).
