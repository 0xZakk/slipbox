---
title: "shift and unshift: Learning JavaScript's Array Methods by Building Them"
slug: shift-and-unshift-learning-javascripts-array-methods-by-building-them
date_published: 2021-02-24T14:16:36.000Z
date_updated: 2021-02-24T14:26:39.000Z
tags: JavaScript, Programming
excerpt: For the sixth article in this series, I explore shift and unshift. By exploring how to implement these yourself, you can learn a lot about how these array methods work.
---

Now that I’ve covered `pop` and `push` and how they are implemented, it only makes sense to give the same coverage to `shift` and `unshift`. Where as `pop` and `push` add and remove items from the end of an array, `shift` and `unshift` do their work at the beginning.

## How They Work

The `shift` method will remove an item from the beginning of an array and the `unshift` method will add one:

    const numbers = [1, 2, 3, 4]
    
    numbers.shift() // [2, 3, 4]
    
    numbers.unshift(1) // [1, 2, 3, 4]
    

In the above snippet of code, we remove the first item (`1`) with `shift`, then add it back to the `numbers` array with `unshift`.

Just like with `push`, you can `unshift` multiple items at once:

    const numbers = [2, 3, 4]
    numbers.unshift(0, 1) // [0, 1, 2, 3, 4]
    

## Removing Without shift

Our `shift` method is going to look a lot like our implementation of `pop`. We want to add every item, except the first one, to a new array. That effectively removes the item, because it will be excluded from the array our `shift` method returns.

Just like with `pop`, we can do this with a loop or we can do this with `slice`. There are actually two ways we can do this with a `for` loop, both of which give us the opportunity to cover some of the really cool properties of loops. We’ll start there and discuss `slice` afterwards.

The first implementation will use a standard loop, modified slightly by a little math:

    function shift (arr) {
    	let res = []
    	for (let i = 0; i < arr.length - 1; i++) {
    		res[i] = arr[i + 1]
    	}
    
    	return res
    }
    

This isn’t so different from your standard loop, nor is it that different from our implementation of `pop`. We start the incrementer (`i`) at `0`. Just like with `pop`, we want to skip one value, so we continue for one less than the length of the array (`arr.length - 1`). We use the index, `i`, as the position in our new array. But we want to assign it to the item in the next position in the passed in array, `arr`.

Compare that to our implementation of `pop`:

    function pop(arr) {
      let res = []
      for (let i = 0; i < arr.length - 1; i++) {
        res[i] = arr[i]
      }
      
      return res
    }
    

It’s very similar, we’re just grabbing the next item (`array[i + 1]`).

And here is how you would use it:

    let numbers = [1, 2, 3, 4]
    
    numbers = shift(numbers) // [2, 3, 4]
    

I find that math like this, while not particularly complicated on its own, makes these loops difficult to read and reason through. You would definitely want to add comments to this so that someone else would understand why you’re subtracting from the array’s length while adding to the incrementer. Otherwise, someone would probably come across this and think it was a mistake.

We can reproduce the effect with a loop that is slightly easier to read by adding a second incrementer:

    function shift(arr) {
      let res = []
      for (let i = 0, j = 1; j < arr.length; i++, j++) {
        res[i] = arr[j]
      }
      
      return res
    }
    

I’ve created an incrementer `i` to track our position in the `res` array and a second incrementer `j` to track our position in `arr`. We increment both of these with each round of the loop.

This is a cool feature of arrays in JavaScript. It makes our code a little easier to understand, but you’d still want to document why you are incrementing two variables instead of one.

With all that said, by far the best approach here is to just use `slice`:

    function shift(arr) {
      return arr.slice(1, arr.length)
    }
    

I mean, just look at how clean that is compared to our two loops? It works, too:

    let numbers = [1, 2, 3, 4]
    numbers = shift(numbers) // [2, 3, 4]

Case closed. Let’s look at `unshift`.

## Adding Without unshift

There are multiple ways to add an item to the end of an array without using `push`. One of the simplest is to just assign a value to an index:

    const numbers = [1, 2, 3, 4]
    numbers[ numbers.length ] = 5
    

We don’t have the same flexibility when working with the beginning of an array. If we assigned a value to an index that already has a value in the array, we’d be overwriting it, not adding it:

    const numbers = [1, 2, 3, 4]
    numbers[0] = 5 // [5, 2, 3, 4]
    

And JavaScript does some funny things when you try to assign a value to a negative index:

    const numbers = [1, 2, 3, 4]
    numbers[-1] = 5 // [ 1, 2, 3, 4, '-1': 5 ]
    

Not quite what we were going for… So we’re automatically *pushed* into writing our own method. To be clear, that’s what we wanted to do anyway, I just couldn’t pass up the opportunity to make a bad JavaScript pun.

Our implementation of `push` looked like this:

    function push(arr, ...items) {
    	return [
    		...arr,
    		...items
    	]
    }
    

We’re using the rest operator to accumulate all the arguments into an array called `items`. This is what makes it so we can push multiple items into the array at once. Then we’re using the spread operator to drop all the items in `arr` and `items` into a new array, which we return.

We’re going to do the same thing for our implementation of `unshift`, but switch the order of our spread operations:

    function unshift(arr, ...items) {
    	return [
    		...items,
    		...arr
    	]
    }
    

Nice and simple. Instead of putting the items in the existing array first, we’re going to put the items in the `items` array first.

It works too:

    let numbers = [1, 2, 3, 4]
    numbers = unshift(numbers, -1, 0) // [-1, 0, 1, 2, 3, 4]
    

## Conclusion

My hope with this whole series is that you’ll see two things:

1. How powerful loops can be
2. How much easier to read array methods are

These may seem like conflicting goals. But the take away should be this: understand array methods and how to use them and use them as often as you can; when you can’t, write a really dope `for` loop with as many incrementers and crazy looking loop constructs as possible.

In all seriousness, I think you should favor array methods as often as you can. But there will be times when you need something *slightly different* from what an existing method will give you. In these cases, you can write your own and modify the implementation to suit your needs.

I’ve now explored five sets of these array methods. If you enjoyed this one, then there are two things you can do:

The first is to give me a follow on [Twitter](https://twitter.com/zfleischmann), so you won’t miss future articles in this series.

The second is to go and read some of the other articles I’ve written on array methods:

- [`pop` and `push`](https://zkf.io/pop-and-push-learning-javascripts-array-methods-by-building-them/)
- [`forEach`](https://zkf.io/foreach-learn-javascripts-array-methods-by-building-them/)
- [`map`](https://zkf.io/map-learn-javascripts-array-methods-by-building-them/)
- [`concat`](https://zkf.io/concat-learn-javascripts-array-methods-by-building-them/)
- [`filter`](https://zkf.io/filter-learn-javascripts-array-methods-by-building-them/)
