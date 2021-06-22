---
title: "filter: Learn JavaScript's Array Methods by Building Them"
slug: filter-learn-javascripts-array-methods-by-building-them
date_published: 2021-01-04T23:00:00.000Z
date_updated: 2021-04-08T12:44:55.000Z
tags: Programming, JavaScript
excerpt: For the fourth article in the series, we explore the filter method and how we can use it to get just a subset of a large array.
---

As we’ve seen with our implementation of `map`, creating a subset of an array is a very common task in JavaScript. With `map`, we transform every item in an array. With `filter`, we get a subset of an array based on some condition.

This is the fourth article in a series where I explain JavaScript’s built-in array methods, specifically focusing on how they work and how to build your own. In the 4 years I spent teaching hundreds of people how to code, I found that thinking through how these array methods work is what would ultimately make them click for people learning JavaScript. `filter` is a powerful method to have in your toolbox, so let’s explore how it works.

## How it Works

The `filter` method takes a callback and invokes it on each item in an array. It then tests if the return value from the callback is truthy. If it is, then it will add the value to a new array. If the return value isn’t truthy, then that value is skipped. At the end, what we’re left with is all the values that returned true when passed into the callback.

For a simple example, let’s get all the even numbers from an array. In JavaScript, we know a number is even if the remainder of dividing it by two is 0 (using the modulo operator):

    // Even numbers
    let num = 6
    if (num % 2 === 0) {
    	console.log(num + " is even!")
    }

We can use this inside a function to test if an argument is an even number:

    function isEven(num) {
    	if (num % 2 === 0) {
    		return true
    	} else {
    		return false
    	}
    }
    
    isEven(6) // true
    isEven(7) // false

Now that we have a function that tests if a number is even or odd, we can use it to test every number in an array by passing it into `.filter()`:

    let nums = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
    
    let evens = nums.filter(isEven)
    
    console.log(evens) // [ 2, 4, 6, 8, 10 ]

The `.filter()` method takes our `isEven` function (as a callback) and invokes it on every item in the array. If `isEven` returns `true`, then we add the current item to a new array; if it returns `false`, then we skip the current item. When `filter()` finishes looping through the `nums` array, it returns the new array of all the items that returned `true` when passed in to `isEven`.

That’s probably a little hard to follow. So instead of explaining it more, let’s implement our own. Seeing the code will help you understand what `filter` is doing better than anything else.

## Implementing Our Own

To implement our own version of the `filter` method, we need to define a function that does the following:

- Accept an array and a callback function as arguments
- Create a new empty array, which we’ll return at the end
- Loop through the array, invoking the callback on each item
- If the callback returns a truthy value, then add the current item to the new array
- If the callback returns a falsey value, then skip adding the current item to the new array
- When the loop is finished, return the new array

We’ll go through this step by step, starting with creating a function, called `filter`, that accepts an array and a callback as arguments:

    function filter(items, cb) {
    	// More to come here ...
    }

Our first argument, `items`, will be the passed in array. The second item, `cb`, will be the callback. (As a side note, `cb` is a common shorthand for *callback* in JavaScript.)

Next, we need to create an empty array, which we’ll return at the end of the function:

    function filter(items, cb) {
    	let final = []
    
    	// More to come here ...
    
    	return final
    }

You can call this array anything you like, as long as it is something that makes sense. Calling this array `final`, as it will be the final result of this function, is a fairly common name in situations like this.

Now that we have our `final` array, we need to create a loop that will go through each item in the `items` array. We’ll use this look to pass each item in the `items` array into our `cb` callback.

    function filter(items, cb) {
    	let final = []
    
    	for (let i = 0; i < items.length; i++) {
    		// More to come here ...
    	}
    
    	return final
    }

Within this loop, we want to invoke our callback function (`cb`) on the current item in the loop:

    function filter(items, cb) {
    	let final = []
    
    	for (let i = 0; i < items.length; i++) {
    		// Get the current item
    		let currentItem = items[i]
    
    		// Pass it into `cb`
    		let res = cb(currentItem)
    
    		// More to come here ...
    	}
    
    	return final
    }

We’re now getting the current item from the `items` array (based on the index value of `i`) and passing it into the callback (`cb`). We capture the return value of `cb` in the variable `res`. You can also call this variable anything, though `res` is fairly common here too (it’s short for *result*).

We’re almost finished. All that’s left is to test the return value (`res`) to see if it’s truthy or not. If it is, we’ll add it to the `final` array, and if it’s falsey, we’ll skip it:

    function filter(items, cb) {
    	let final = []
    
    	for (let i = 0; i < items.length; i++) {
    		let currentItem = items[i]
    		let res = cb(currentItem)
    
    		if (res) {
    			final.push(currentItem)
    		}
    	}
    
    	return final
    }

That’s it! That’s all we need to do. We don’t need an `else` because we don’t want to do anything if `res` is falsey. We wouldn’t have anything to put in an `else` block!

We can test out our own `filter` method using the `isEven` function that we defined above:

    let nums = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
    
    let evens = filter(nums, isEven)
    
    console.log(evens) // [ 2, 4, 6, 8, 10 ]

We get the same result. Let’s also test it out with a function that gets the odd numbers:

    function isOdd(num) {
    	if (num % 2 !== 0) {
    		return true
    	} else {
    		return false
    	}
    }
    
    let odds = filter(nums, isOdd)
    
    console.log(odds) // [ 1, 3, 5, 7, 9 ]

You can see here that it works with our `isOdds` function as well.

## `filter` in Action

The `filter` method is easily the best way to get a subset of a list, which is a fairly common task in JavaScript development. One place that I use it a lot is to get a section of an API response.

Let’s look at an example. Let’s say we’re building an application for managing candidates who’ve applied for a job. To do that, we want to be able to filter, within the user interface, for developers with certain experience levels and skills. We might have a page in the application that looks something like this:

![](https://zkf.io/content/images/2021/02/filter-user-interface.png)

The left sidebar has some filters (in this case, experience and programming languages). When someone clicks on one of these filters, the contents of the main area of the screen should change to only those that match these filters. We can use the `filter` method for that.

If the data we get back from the API looks like this:

    const developers = [
      {
        name: "Antonio",
        experience: "Junior",
        language: "JavaScript"
      },
      {
        name: "José",
        experience: "Senior",
        language: "JavaScript"
      },
        {
        name: "Carmen",
        experience: "Junior",
        language: "Python"
      },
        {
        name: "Mercedes",
        experience: "Junior",
        language: "JavaScript"
      },
        {
        name: "Ana",
        experience: "Junior",
        language: "JavaScript"
      },
    ]

Then we can filter for all the junior developers with something like this:

    function isJunior(developer) {
    	if (developer.experience === "Junior") {
    		return true
    	}
    	
    	return false
    }
    const juniorDevelopers = developers.filter(isJunior)

This will give us Antonio, Carmen, Mercedes, and Ana.

We could do something similar for JavaScript developers:

    function knowsJavaScript(developer) {
    	if (developer.language === "JavaScript") {
    		return true
    	}
    
    	return false
    }
    
    const javascriptDevelopers = developers.filter(knowsJavaScript)

Our `javascriptDevelopers` array now has Antonio, José, Mercedes, and Ana in it.

And if we want to `filter` for junior developers and JavaScript developers, we can do that too:

    const currentDevelopers = developers.filter(function (developer) {
    	if (
    		developer.language === "JavaScript" &&
    		developer.experience === "Junior
    	) {
    		return true
    	}
    
    	return false
    })

All that would be left now to build out our page in the candidate tracking app is to render this array of developers to the screen!

## Conclusion

I’ve now covered four of JavaScript’s built-in array methods. If you haven’t already, definitely check out the other articles in this series:

- [`forEach`](https://zkf.io/js-array-methods-foreach/)
- [`map`](https://zkf.io/js-array-methods-map/)
- [`concat`](https://zkf.io/js-array-methods-concat/)

I’m going to go through and explain and implement every built-in array method. If you’re struggling to learn them, or just want to learn more about JavaScript in general, then be sure to follow along by signing up for my [newsletter](https://hawthorne.substack.com/) and following me on [Twitter](https://twitter.com/ZFleischmann).
