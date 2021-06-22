---
title: "every and some: Learning JavaScript's Array Methods by Building Them"
slug: every-and-some-learning-javascripts-array-methods-by-building-them
date_published: 2021-03-24T13:20:31.000Z
date_updated: 2021-03-24T13:20:31.000Z
tags: JavaScript
excerpt: This article walks through how to use and implement the every and some array methods in JavaScript.
---

I’ve made a lot of progress on the list of array methods, having covered eight so far. In this article, I’ll cover two more: `every` and `some`, both of which are great methods for understanding the contents of an array.

## How They Works

It’s pretty common to want to test the contents of an array before running some code against it. Perhaps you need to check that every user is active before starting the game loop in an online game. In JavaScript-speak, you want to check that the `active` property is set to `true` for every `user` object in the array of users. This is where the `every` method comes in handy: it will return `true` or `false` based on a test function.

The `every` method checks that *every* object passes the test; the `some` method checks that at least one object passes the test (i.e. that *some* of them do). So if you need at least one user to be a host for the game to start (i.e. at least one `user` object in the users array needs to have a `host` property of `true`) you can use `some` to check for that.

### The every Method

Thinking back, my implementation of the `concat` method took any number of arrays supplied as arguments and merged them together into a single array. There is one small issue with my implementation though: it doesn’t check that all the values passed in are in fact arrays:

    function concat(...args) {
      let final = []
    
      args.forEach(arg => {
        final = [ ...final, ...arg ]
      })
    
      return final
    }
    

I can fix this quickly and easily with the `every` method:

    function concat(...args) {
      let areArrays = args.every(arg => Array.isArray(arg))
      if (!areArrays) return new Error("Every argument must be an array.")
    
      // Rest of code ...
    }

Now, if someone tries to pass in a value that isn’t an array, they’ll get an error back:

    concat([1,2,3], 'a', [4, 5, 6])
    // Error: 'Every argument must be an array.'
    

This is very simple error handling, but it will save my users from receiving an error that doesn’t make sense.

The important part that makes all this work is the arrow function I’m passing in to the `every` method. That method must return a boolean value, which determines the final output. If every invocation of this function returns `true` (or a truthy value), then the call to `every` will return `true`. If any one invocation does not return `true`, then `every` will return `false`.

### The some method

The `some` method will return true if *any* item passes the test function. That is, if any of the test function invocations return `true`, then the `some` method will return `true`:

    const vals = ['a', 1, 5, NaN, true, ['h','e','l','l','o'], 'z', 'world']
    vals.some(val => Array.isArray(val)) // true
    

In the above snippet of code, we have a bunch of random values in an array. On the second line, we’re testing that some (so, at least one) of the values is an array. The sixth item in `vals` is an array of strings, so we get `true` back.

I’ll admit here that I rarely find a use for the `some` method. Instead, I tend to test the output of `filter`, because if I need at least one of the values in an array to pass a test, I probably also need those specific values back. The `filter` method lets me do both at once. If the output array of `filter` has a length of `0`, then I know that no items passed my test function and can display that fact to the user. If any of them did pass the test, I now already have those values.

## Implementing Our Own

We’ll start by implementing the `every` method and then move on to implementing the `some` method. Both implementations will look pretty similar, which is why we’re treating them both together in this article. There is only one small difference in the internal logic that makes them work.

### Implementing every

To start off, I need a function that accepts an array and a callback. The callback will get invoked on every item in the array, which is how I’ll calculate our result:

    function every(vals, cb) {
      // More here later 
    }
    

Next, I need to loop through `vals` and check that invoking `cb` on each value returns `true`, or a truthy value:

    function every(vals, cb) {
      
      for (let i = 0; i < vals.length; i++) {
        let res = cb( vals[i] )
        // More here later
      }
    
    }
    

I’ve got a standard `for` loop that gets the current value of the array and passes it into the `cb` callback function, capturing the result in `res`.

Now, if `res` is ever `false` or falsey, I want to return `false`. I can do that with a simple conditional:

    function every(vals, cb) {
    
      for (let i = 0; i < vals.length; i++) {
        let res = cb( vals[i] )
        if (!res) return false
      }
    
    }
    

If `res` is every false (or, not true) then we return `false` immediately. I want to make it so by default we return `true`, so I can add that too:

    function every(vals, cb) {
    
      for (let i = 0; i < vals.length; i++) {
        let res = cb( vals[i] )
        if (!res) return false
      }
      
      return true
    }
    

And we’re set:

    const vals1 = [1, 2, 3, 4, 5]
    const vals2 = [1, 2, '3', 4, 5]
    const isNumber = val => typeof val === 'number'
    
    every(vals1, isNumber) // true
    every(vals2, isNumber) // false
    

My first array of values only includes numbers in it, so it returns `true` when we pass it into our implementation of `every` with the test function `isNumber`. By contrast, the second array of values has a string in it (`'3'`), so it returns `false`.

### Implementing some

My implementation of `every` checks that every value passes the test function; my implementation of `some` needs to check that *any* value passes the test function. The implementation will be very similar, but with a small tweak.

To start, I need a function, called `some` that accepts an array and a callback function:

    function some(vals, cb) {
      // More here later
    }
    

Then, we need to loop through the `vals` array and pass each value to the `cb` function, just like in our implementation of `every`:

    function some(vals, cb) {
      
      for (let i = 0; i < vals.length; i++) {
        let res = cb( vals[i] )
    	// More here later
      }
      
    }
    

This is the part where things become a little different: I’m going to reverse the order of my return values. If `res` is `true` (or truthy), then I’m going to return `true` from `some`. Otherwise, I’m going to return `false` from `some`:

    function some(vals, cb) {
      
      for (let i = 0; i < vals.length; i++) {
        let res = cb( vals[i] )
        if (res) return true
      }
      
      return false
    }
    

I’ll use this to test if any of the values in the previous two arrays are strings:

    const vals1 = [1, 2, 3, 4, 5]
    const vals2 = [1, 2, '3', 4, 5]
    const isString = val => typeof val === 'string'
    
    some(vals1, isString) // false
    some(vals2, isString) // true
    

The first array only contains numbers, so my invocation of `some` returns false (no value is a string). My second invocation returns true because one of the values in `vals2` is a string (`'3'`).

## Conclusion

If you’ve been following along with this series of articles then you’ll see, once again, that these methods are a lot simpler and easier to implement than you might initially think.

As I was planning out this article, I assumed I would need a flag value in `every` and `some` in order to make my implementations work. A `flag` value is a variable you set at the beginning of the function definition and use to exit out of the function if it every changes.

That ended up being too complicated for what I needed, so I’ll have to explain it in a future article. But you can see how it’s easy to over-complicate what these methods do.

These are the seventh and eighth array methods I’ve written about. If you enjoyed this one, then there are two things you can do:

The first is to give me a follow on [Twitter](https://twitter.com/zfleischmann), so you won’t miss future articles in this series.

The second is to go and read some of the other articles I’ve written on array methods:

- [`shift` and `unshift`](https://zkf.io/shift-and-unshift-learning-javascripts-array-methods-by-building-them/)
- [`pop` and `push`](https://zkf.io/pop-and-push-learning-javascripts-array-methods-by-building-them/)
- [`forEach`](https://zkf.io/foreach-learn-javascripts-array-methods-by-building-them/)
- [`map`](https://zkf.io/map-learn-javascripts-array-methods-by-building-them/)
- [`concat`](https://zkf.io/concat-learn-javascripts-array-methods-by-building-them/)
- [`filter`](https://zkf.io/filter-learn-javascripts-array-methods-by-building-them/)
