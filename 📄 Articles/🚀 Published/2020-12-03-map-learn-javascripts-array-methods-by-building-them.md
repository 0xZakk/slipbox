---
title: "map: Learn JavaScript's Array Methods by Building Them"
slug: map-learn-javascripts-array-methods-by-building-them
date_published: 2020-12-04T00:00:00.000Z
date_updated: 2021-04-08T12:44:23.000Z
tags: Programming, JavaScript
excerpt: Next in the series exploring JavaScript's array methods - map. Perhaps one of the most commonly used and powerful of JavaScript's array methods.
---

JavaScript's `map` method is a powerful method for working with arrays and one of the most commonly used. You'll likely see it used all over a React codebase to turn an array of data from an API into an array of components. It's also just a small step up in complexity from `forEach`, which we covered [previously](http://localhost:8000/js-array-methods-foreach/).

This article is part of a series of articles where I explain JavaScript's built-in array methods. This article focuses on the `map` method, which is used to create a new array based an existing one. I'll describe how it works and when to use it, but most of the article will focus on implementing `map` for yourself.

## How it Works

The `map` method takes an existing array and a function and executes the function on each item of the array. This is just like the `forEach` method, but there is one key difference between `forEach` and `map`: the `map` method returns a new array based on the result of executing the passed in function. There's a subtle requirement for the the function passed into `map`: it has to return something, so that `map` can add it to the array it creates for us.

A technical way of describing `map` is: it creates a *derivative* array based on a function:

    const numbers = [1, 2, 3, 4, 5]
    
    function doubleNumber(number) {
    	return number * 2
    }
    
    const doubles = numbers.map(doubleNumber)
    console.log(doubles) // [2, 4, 6, 8, 10]

We start with an array of numbers called `numbers` and a function called `doubleNumber` that takes an argument and returns its double value (the result of multiplying it by 2). By passing `doubleNumber` into `map`, we're saying, "invoke this function on each item in the `numbers` array," which results in the array `[2, 4, 6, 8, 10]` (or original array, `numbers` contains the values `[1, 2, 3, 4, 5]`).

It's important to remember that *every* array method can be implemented with a `for` loop, including `map`.

A beginner might approach the task of doubling each item in an array with something that looks like this:

    const numbers = [1, 2, 3, 4, 5];
    const doubles = []
    
    for (let i = 0; i < numbers.length; i++) {
      let number = numbers[i]
      let double = number * 2
      doubles.push(double)
    }
    
    console.log(doubles) // [2, 4, 6, 8, 10]

We can simplify this a bit by turning the actual "action" we're performing into it's own function and bringing back our `doubleNumber` function:

    const numbers = [1, 2, 3, 4, 5];
    const doubles = []
    
    function doubleNumber(number) {
      return number * 2
    }
    
    for (let i = 0; i < numbers.length; i++) {
      let number = numbers[i]
      let double = doubleNumber(number)
      doubles.push(double)
    }
    
    console.log(doubles) // [2, 4, 6, 8, 10]

This actually brings us very close to our own implementation of `map`.

## Implementing Our Own

We said earlier that `map` is used to create a *derivative* array:

    const numbers = [1, 2, 3, 4, 5]
    
    function doubleNumber(number) {
    	return number * 2
    }
    
    const doubles = numbers.map(doubleNumber)
    console.log(doubles) // [2, 4, 6, 8, 10]

This code snippet from before starts with an array, `numbers` and uses `map` and the function `doubleNumbers` to create the `doubles` array.

Based on how we're using it here, we can determine that the requirements for the `map` method are:

- A function that takes an array and a function
- Invokes the passed in function on each item in the passed in array
- Stores the result of the function call in a new array
- Returns the new array

Starting with the first requirement, we can create a function called `map` that takes an array and a function as arguments:

    function map(arr, fn) {
      // more to come here
    }

Then, we want to loop through the array, using basically the same loop we used above, so that we can invoke the passed in function on each item in the next step:

    function map(arr, fn) {
      for (let i = 0; i < arr.length; i++) {
    	  // more to come here
      }
    }

Now we pass each item in the array into `fn`:

    function map(arr, fn) {
      for (let i = 0; i < arr.length; i++) {
    	  let item = arr[i]
    	  let newItem = fn(item)
      }
    }

We've got the new value from our function. Based on the requirements, we need to store it into an array and return that array:

    function map(arr, fn) {
    	const final = []
    
      for (let i = 0; i < arr.length; i++) {
    	  let item = arr[i]
    	  let newItem = fn(item)
    
    	  final.push(newItem)
      }
    
      return final
    }

That's all there is to it!

Doubling each item in an array with our `map` function would now look like this:

    const numbers = [1, 2, 3, 4, 5, 6];
    
    const doubles = map(numbers, doubleNumber)
    console.log(doubles) // [2, 4, 6, 8, 10, 12]

Just like with `forEach`, this is much easier to read and understand than writing out the full `for` loop.

## `map` in Action

Now that we've implemented `map` for ourselves, we can explore its use a little bit more. I typically use `map` for one of two things: *transforming* an array of data or *extracting* data from an existing array.

I'll walk you through examples of both using the following data:

    const profiles = [
      {
        name: "Mercedes",
        profession: "Software Engineer"
      },
      {
        name: "Antonio",
        profession: "Front-end Developer"
      },
      {
        name: "Ana",
        profession: "Back-end Developer"
      }
    ]

This array contains objects representing engineers where each engineer's profile contains their name and their profession.

### Transforming Data

The `doubles` example from above is a simple example of using `map` to transform data. Our data typically isn't that simple though. So a more complex example would be to take our `profiles` array and create a new array of descriptions for each engineer.

    const descriptions = map(profiles, function createDescription(profile) {
      let {name, profession} = profile
      return `${name} is a ${profession}`
    })
    
    console.log(descriptions) // [ 'Mercedes is a Software Engineer', 'Antonio is a Front-end Developer', 'Ana is a Back-end Developer' ]

In the above snippet of code, we take our array of profiles and `map` over it with the `createDescription` function, which takes a profile and returns a string `"<name> is a <profession>"`. Now we have an array of profiles and a separate array with each engineer's description.

We can modify this slightly to instead give us a new array of profiles where each profile includes the description. This is often even more helpful:

    map(profiles, function createDescription(profile) {
      let {name, profession} = profile
      return {
    	  ...profile,
    	  description: `${name} is a ${profession}`
      }
    })

This code would produce an array that looks like this:

    [
      {
        name: 'Mercedes',
        profession: 'Software Engineer',
        description: 'Mercedes is a Software Engineer'
      },
      {
        name: 'Antonio',
        profession: 'Front-end Developer',
        description: 'Antonio is a Front-end Developer'
      },
      {
        name: 'Ana',
        profession: 'Back-end Developer',
        description: 'Ana is a Back-end Developer'
      }
    ]

### Extracting Data

Another common way to use `map` is to extract data into a separate array. For instance, we can take our `profiles` array and create an array of just the names:

    const names = map(profiles, function getProfileNames(profile) {
      return profile.name
    })
    
    console.log(names)

This is really common when an API gives you a lot of data that you don't need. I find myself doing something like this a lot when I'm working with charting libraries and data from APIs. The data from the API comes back in the format determined by the API's schema and I need to extract some and transform it into a format that will work with the charting library.

## Conclusion

That concludes my discussion of `map`. If you haven't read the similar discussion of `forEach`, then you can find it [here](https://zkf.io/js-array-methods-foreach/). I'm going to go through and explain and implement every built-in array method, which will help you understand how they work and when and how to use them. To follow along, sign up for my [newsletter](https://hawthorne.substack.com/) and follow me on [Twitter](https://twitter.com/ZFleischmann).
