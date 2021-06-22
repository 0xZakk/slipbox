---
title: "pop and push: Learning Javascript's Array Methods by Building Them"
slug: pop-and-push-learning-javascripts-array-methods-by-building-them
date_published: 2021-02-03T00:00:00.000Z
date_updated: 2021-04-08T12:45:11.000Z
tags: Programming, JavaScript
excerpt: I explore implementing pop and push in the fifth article of this series. Specifically, how can we add an item without using push or remove an item without using pop?
---

The array methods that I’ve covered so far in this series have been focused on looping through an array for some purpose: doing something to each item, getting a modified version each item, or getting a slice of the array. That includes looking at `forEach`, `filter`, and `map`.

In this article, I’d like to focus on another way of working with arrays. Specifically, `pop` and `push`, which are used for adding and removing items from an array.

Just like in my previous articles, I am going to walk through how to implement your own versions of `pop` and `push`. With that said, 90% of the time, you’ll want to use these built in methods. The purpose of looking at how to implement your own is to understand how to get the same functionality in cases where you can’t use `pop` and `push`. For example, in parts of building a React application where state is immutable (can’t be changed).

## How They Work

You use `push` to add an item to the end of an array and `pop` to remove an item from the end of an array:

    const numbers = [1, 2, 3, 4]
    
    // Add an item to the end:
    numbers.push(5) // [1, 2, 3, 4, 5]
    
    // Removethe last item:
    numbers.pop() // [1, 2, 3, 4 ]

Here I’m taking an array (`numbers`) and adding an item (`5`) to the end with `push`. Then, I immediately remove it with `pop`.

There are separate, corresponding methods for adding and removing from the beginning of array. These are `shift` and `unshift` and I’ll cover these in a future article.

## Adding Without Using `push`

How can you add an item to the end of an array without using the `push` method?

The easiest way is to assign a value to an index position within the array:

    const numbers = [1, 2, 3, 4]
    numbers[ numbers.length ] = 5

Not every programming language lets you do this. Generally, arrays are of fixed length and you would actually have to create a new, longer array with the new value. This is true in Go, for example.

JavaScript will let you do this most of the time. But, there are two limitations to this approach. First, you’re now managing the indices of this array manually. Double check your code to make sure you don’t miss an index somewhere or have any off-by-one issues. Second, as I mentioned earlier, there are times when you want to (or need to) create a new array.

You can do create a new array with the added item using the spread operator, which I covered in my implementation of [`concat`](https://zkf.io/js-array-methods-concat/). With the spread operator, I can implement my own version of `push` that mimics the same behavior.

To do so, I need to define a function that takes an array and the new item as arguments. Then, it needs to return a new array with all the values of the original array, plus the new item. Something like this:

    function push(array, item) {
    	return [
    		...array,
    		item
    	]
    }

Now, with my original `numbers` array, I can do something like this:

    let numbers = [1, 2, 3, 4]
    
    numbers = push(numbers, 5) // [1, 2, 3, 4, 5]

This implementation is missing one thing: the built-in `push` method lets you add multiple values at once:

    let numbers = [1, 2, 3, 4]
    
    numbers.push(5, 6, 7) // [1, 2, 3, 4, 5, 6, 7]

Modifying my implementation to accommodate this is actually fairly simple with the spread and rest operator:

    function push(array, ...items) {
    	return [
    		...array,
    		...items
    	]
    }

On line 1, I’m taking any number of arguments after the initial array and merging them into an array called `items` using the rest operator. I then use the `spread` operator to drop these items into the new array, along with the items in the passed in array.

(Note that it can be a little confusing when `...` is doing a spread operation versus a rest operation. It’s even more confusing that this operator works with Objects too!)

Now my implementation can take any number of arguments after the original array:

    let numbers = [1, 2, 3, 4]
    
    // Adding one new item:
    numbers = push(numbers, 5) // [1, 2, 3, 4, 5]
    
    // Adding more than one:
    numbers = push(numbers, 6, 7, 8) // 1, 2, 3, 4, 5, 6, 7, 8]

## Removing without Popping

Removing the last item from an array without using `pop` is a little tricky. The best approach will depend a bit on your circumstances and will probably involve another array method. I’ll show you one approach that doesn’t work as well as you’d think, one that works alright, and then the one I think is best.

If you’ve come across `delete` in JavaScript, you may jump to that as one approach. I would generally recommend avoiding `delete` though. In this case, it will delete the item from the array, but a behavior that you might not expect is that the length of the array will stay the same and there will be an empty item (or slot) left at the end:

    let numbers = [1, 2, 3, 4]
    
    // The original length:
    numbers.length // 4
    
    // Delete the last item:
    delete numbers[ numbers.length - 1]
    
    // The new length:
    numbers.length // 4
    
    numbers // [1, 2, 3, <1 empty slot>]

If you were to later loop over this array, the length wouldn’t correspond to the number of actual values in the array and you’d get some weird, hard-to-debug behavior:

    for (let i = 0; i < numbers.length; i++) {
        console.log(numbers[i])
    }
    // 1
    // 2
    // 3
    // undefined

Another approach would be to write a `for` loop that creates a new array. I can do this inside a function to mimic the behavior of `pop`:

    function pop(array) {
      let res = []
      for (let i = 0; i < array.length - 1; i++) {
        res[i] = array[i]
      }
      
      return res
    }

In the `pop` method above, I take the original array as an argument. I then immediately create a new empty array that I will eventually return back to the caller. I then loop over the original array, but skip the last item (`i < array.length -1`) which effectively deletes it. Inside the body of this loop, I assign the value in the current position of the passed in array to the position of the new array (`res[i] = array[i]`).

This works just fine:

    let numbers = [1, 2, 3, 4]
    
    numbers = pop(numbers) // [1, 2, 3]

This does continue to support my theory that every array method can be implemented with a `for` loop. But, as I have also said previously in this series, you generally want to avoid `for` loops and instead use a named method so your code easier to read. The same is true here, but with a small caveat.

I can accomplish the same goal using `slice` and skip the loop. The caveat is that a lot of people have trouble (reasonably so) remembering the difference between `slice` and `splice`. I found learning Go helped me. A Slice in Go is a data structure equivalent to an Array in JavaScript, where an Array in Go acts like the more traditional Array-type. Arrays in Go have a fixed length that can’t be changed after initialization. Otherwise, I haven’t heard a good mnemonic for remembering the difference.

At any rate, I can really simplify the implementation of my `pop` method by using `slice`:

    function pop(array) {
      return array.slice(0, array.length - 1)
    }

A future article in this series will walk through implementing both `slice` and `splice`. In the meantime, you need to know that the arguments passed in are the starting and ending positions for the slice. `slice` then returns a shallow copy of this portion of the array.

Using the new version of my `pop` method, I can get the same result:

    let numbers = [1, 2, 3, 4]
    
    numbers = pop(numbers) // [1, 2, 3]
    numbers = pop(numbers) // [1, 2]
    numbers = pop(numbers) // [1]

Of the three approaches to this problem, using `slice` is the best option. I am the one writing a whole series on every array method though, so I may have a biased affinity for them.

## Conclusion

This is the fourth article in a series going through each of the built-in array methods in JavaScript. If you haven’t already, definitely check out the other articles in this series:

- [`forEach`](https://zkf.io/js-array-methods-foreach/)
- [`map`](https://zkf.io/js-array-methods-map/)
- [`concat`](https://zkf.io/js-array-methods-concat/)
- [`filter`](https://zkf.io/js-array-methods-filter/)

I’m going to go explain and implement every built-in method. If that’s interesting to you, I’d encourage you to follow me on [Twitter ](https://twitter.com/ZFleischmann)so you don’t miss future articles in this series.
