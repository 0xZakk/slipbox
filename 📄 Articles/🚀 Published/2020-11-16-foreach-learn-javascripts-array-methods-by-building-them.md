---
title: "forEach: Learn JavaScript's Array Methods by Building Them"
slug: foreach-learn-javascripts-array-methods-by-building-them
date_published: 2020-11-17T00:00:00.000Z
date_updated: 2021-04-08T12:44:00.000Z
tags: Programming, JavaScript
excerpt: First in a series of articles exploring JavaScript's array methods, including a walk through of how to build your own. This article covers the forEach method.
---

JavaScript's array methods are really powerful tools for writing code that is expressive and easy to read. But for beginners, they can be difficult to understand. Once you're comfortable with loops, `forEach` is a great first array method to learn because it is just a small abstraction over a single `for` loop.

This article is part of a series I'll be doing where I explain JavaScript's built-in array methods. I'll describe how and when to use them as well as how to implement them yourself. The goal of implementing the array methods yourself is to help you understand what's going on under the hood. So when you want to use `map` or see a code block that is using `reduce`, you'll be able to understand what's going on.

Developing a deeper understanding of JavaScript's array methods is a great way to improve the readability of your code. Every array method is an abstraction over a `for` loop, meaning anything you can do with an array method can be done with a `for` loop, and vice versa. The difference is that array methods make your code a lot more readable by making it more expressive.

I think of learning new programming language constructs as similar to learning new categories of vocabulary of a foreign language. If you learned Spanish or French in school, then you probably had lessons dedicated to asking for directions, ordering food at a restaurant, or interviewing for a job. In these lessons, you learned words and phrases that were more likely to come up in those specific settings so that you could better express yourself.

Sure, you can sit down at a restaurant and ask for "the plate with green stuff on it," ("el plato con cosas verdes") but the waiter will have an easier time understanding what you mean if you just say "a salad, please" ("una ensalada, por favor").

Learning this vocabulary helps you express yourself more clearly, just as learning programming language constructs helps you write more expressive code for particular kinds of problems. JavaScript's array methods will help you write more expressive code when working with arrays. The effect is the same: other developers, including your future self, will have a better idea of what you mean.

I'm going to go through every built-in array method and explain what it does and how to use it, as well as show you how it works by explaining how you could implement it yourself. If that sounds like something you're interesting in, follow along by signing up for my [newsletter](https://hawthorne.substack.com/) and following me on [Twitter](https://twitter.com/ZFleischmann).

Let's get into it

## How it Works

We're starting with `forEach` because it is the lightest abstraction over a standard `for` loop. A common task when working with arrays is to loop through and perform some action on each item in the array. For example, you might do something like this:

    const numbers = [1, 2, 3, 4, 5, 6];
    
    for (let i = 0; i < numbers.length; i++) {
      let number = numbers[i]
      console.log(number)
    }

In the above snippet of code, we create an array of numbers (called `numbers`), then create a `for` loop to go through each item in the array. Within the `for` loop, we simply grab the current item and `console.log` it.

If we wanted to make the above snippet of code slightly more abstract, we could modify it to look like this:

    const numbers = [1, 2, 3, 4, 5, 6];
    
    function printNumber(number) {
      console.log(number)
    }
    
    for (let i = 0; i < numbers.length; i++) {
      let number = numbers[i]
      printNumber(number)
    }

Here we've created a function called `printNumber` that takes a number and prints it to the console. The important point is that this function does whatever action we're performing on each item of the array. In this specific example, that just means print it. We'll come back to this function in a bit though.

## Implementing Our Own

As the name suggests, the `forEach` method loops through an array and runs a function *for each* item in the array (just like our previous snippet of code). We're actually really close to the implementation of `forEach` already.

To implement our own `forEach` method, we need to define a function that takes an array and a function, loops through the array, and passes each item into the function.

Let's start by defining our function:

    function forEach(arr, fn) {
      // more to come here ...
    }

We've declared a function called `forEach` that takes two arguments: an array called `arr` and a function called `fn`.

Next, we want to loop through every item in the array:

    function forEach(arr, fn) {
      for (let i = 0; i < arr.length; i++) {
        // more to come here ...
      }
    }

We've added a `for` loop that goes through the passed in array. Note this is the exact same `for` loop that we had above.

Now all that's left to do is to get the current item and pass it into the function, `fn`:

    function forEach(arr, fn) {
      for (let i = 0; i < arr.length; i++) {
        let item = arr[i]
        fn(item)
      }
    }

And there you have it! Now you can see it all together:

    const numbers = [1, 2, 3, 4, 5, 6];
    
    function printNumber(number) {
      console.log(number)
    }
    
    function forEach(arr, fn) {
      for (let i = 0; i < arr.length; i++) {
        fn(arr[i])
      }
    }
    
    forEach(numbers, printNumber)

## `forEach` in Action

Now that we have our `forEach` method defined, it's just a matter of modifying the function that we pass in to the items in `numbers`.

We could, for instance, double each number in `numbers`:

    function doubleNumber(number) {
    	console.log(number * 2)
    }
    
    forEach(numbers, doubleNumber)

Alternatively, we could use `forEach` to get uppercased versions of an array of strings:

    const names = ["Mercedes", "Antonio", "Sergio", "José", "Ana", "Carmen", "Dolores"]
    
    function uppercaseName(name) {
    	console.log(name.toUpperCase())
    }
    
    forEach(names, uppercaseName)

## Why Array Methods

The goal of JavaScript's array methods is to provide built-in methods for common tasks and to help you write more readable code. Any `for` loop requires really looking at and reading the code in order to understand what it's doing. We can change the meaning of a `for` loop a lot by just changing a few characters:

    for (let i = 0; i < numbers.length; i++) {
      let number = numbers[i]
      console.log(number)
    }
    
    for (let i = numbers.length; i > 0; i--) {
      let number = numbers[i]
      console.log(number)
    }

Here we have two `for` loops that are nearly identical, but one loops through the array backwards (from last index to first). You can see the difference when you read through the code, but it's not immediately obvious at first glance. Also, the construct of the loop isn't the important part of this block of code, the body is, so we don't want to have to spend time reading and understanding it.

Think back to the Spanish restaurant and our plate with green stuff on it. The waiter is going to have to check if you mean the salad or the side order of asparagus, just like we have to check what this loop is doing. It's easier for everyone if we just learn how to ask for a salad.

When we say we want our code to be easy to read, we mean we want it to be easy to understand what it is doing at first glance and without taking the time to work through the syntax piece by piece. Using array methods, like `forEach`, makes this a lot easier:

    const numbers = [1, 2, 3, 4, 5, 6];
    
    function printNumber(number) {
      console.log(number)
    }
    
    forEach(numbers, printNumber)

## Conclusion

That concludes my discussion of `forEach`. I hope that you found it helpful, but I also hope that you found the implementation of `forEach` fairly simple. I find a lot of JavaScript developers haven't thought about how these methods are implemented. When you do, you see that they're all pretty simple. Going through and thinking about how they're implemented made using them a lot easier, which is what I hope to share with you.

I'm going to go through and explain and implement every built-in array method, which will help you understand how they work and when and how to use them. To follow along, sign up for my [newsletter](https://hawthorne.substack.com/) and follow me on [Twitter](https://twitter.com/ZFleischmann).
