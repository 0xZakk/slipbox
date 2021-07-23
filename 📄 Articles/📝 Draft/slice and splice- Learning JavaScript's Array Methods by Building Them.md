---
title: slice and splice, Learning JavaScript's Array Methods by Building Them
summary: "Article that walks through examples of how to use the slice and splice array method in JavaScript as well as how to implement it it"
---

# `slice` and `splice`- Learning JavaScript's Array Methods by Building Them

In this article, I’ll talk through the `slice` and `splice` array methods. Specifically, how they work, when and how to use them, and how to implement your own.

## How They Work

While their names are similar, they don’t really perform similar functions. The `slice` method will create a shallow copy of a section of an array and the `splice` method modifies the contents of an array by removing, replacing, and/or adding elements. `slice` is the one you’ll probably find more uses for, but `splice` is the more powerful one. 

### The slice Method

The `slice` method takes `start` and `end` values, both of which are optional, and returns a shallow copy of that section of an array:

```javascript
const vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

vals.slice() // Shallow copy the whole array
vals.slice(5) // Shallow copy the last five values
vals.slice(3, 6) // Shallow copy the middle 3 values
```

In this snippet of JavaScript, we have an array of numbers called `vals`. On line 3, our first call to `slice` creates a shallow copy of the _entire_ array — so we now have two, the original, and a copy. If you ever want a fast way of copying an array, `slice` is actually a good way to do it:

```javascript
const vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

const valsCopy = vals.slice() // Shallow copy the whole array

console.log(vals) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(valsCopy) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Note however that this is pretty hacky. You should either find a more intuitive way of creating a copy or put in a comment that explains why you’re doing it this way. Your future self will thank you.

What you’re more likely to use `slice` for is copying a subsection of an array,  which we see here:

```javascript
const vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

vals.slice(5) // [ 5, 6, 7, 8, 9 ]
vals.slice(3, 6) // [ 3, 4, 5 ]
```

Our first call to `slice` creates a shallow copy of the last four values in the `vals` array. The second call to `slice` creates a copy of the middle three values.

Observe that `vals.slice(5)` returns a copy of the array from the 5th index to the end: `[5, 6, 7, 8, 9]`. That tells us that the first argument is an inclusive index: start at 5 and continue to the end.

Now look at `vals.slice(3, 6)`. Note that our starting value in the return copy is `3`, which makes sense given our previous observation. But see how our second argument is `6` and the last value in our shallow copy is `5`? That’s because the first index is _inclusive_ while the second index is _exclusive_: we return up to, _but not including_ that index.

This is pretty standard behavior for creating a slice. For instance, in Python, you see the exact same behavior:

```javascript
vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(vals[:]) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
print(vals[5:]) # [ 5, 6, 7, 8, 9 ]
print(vals[3:6]) # [ 3, 4, 5 ]
```

And in Go too:

```javascript
func main() {
    vals := []int{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
    fmt.Println(vals[:]) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    fmt.Println(vals[5:]) // [ 5, 6, 7, 8, 9 ]
    fmt.Println(vals[3:6]) // [ 3, 4, 5 ]
}
```

### The splice Method

The `splice` method is used to remove or replace items.

When we called `vals.slice(3, 6)`, we got a shallow copy of the middle of our `vals` array. If we instead wanted to cut these items out of the `vals` array, we could do so with `splice`:

```javascript
const vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

vals.splice(3, 3) // [3, 4, 5]
console.log(vals) // [0, 1, 2, 6, 7, 8, 9]
```

The `splice` method cuts out 3 items (the second argument), starting at index 3 (the first argument). It modifies the original array and returns the spliced section as a new array.

This is probably the cause of most of the confusion between these two methods: `slice` returned a copy while `splice` modified the existing array. If you’re not expecting that, then you would probably get some hard-to-track-down bugs when suddenly your array is shorter than you expected and some of the values are missing!

#### How to Use splice

`splice` takes at least two arguments: the starting index and the number of items to be spliced. We saw this in the previous example:

```javascript
const vals = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

vals.splice(3, 3) // [3, 4, 5]
console.log(vals) // [0, 1, 2, 6, 7, 8, 9]
```

The first value is the starting index and the second is the number of items to be spliced (or removed).

The starting index is where we make the cut in the array. The number can be negative, in which case the cut will be from the end of the array.

If we want to cut the array from the 5th index:

```javascript
vals.splice(5) // [ 4, 5, 6, 7, 8, 9 ]
console.log(vals) // [ 0, 1, 2, 3 ]
```

If you want to quickly cut an array in half:

```javascript
vals.splice( vals.length / 2 ) // [ 5, 6, 7, 8, 9 ]
console.log(vals) // [ 0, 1, 2, 3, 4 ]
```

If you want to make a cut from the end of the array:

```javascript
vals.splice( -4 ) // [ 6, 7, 8, 9 ]
console.log(vals) // [ 0, 1, 2, 3, 4, 5 ]
```

You can see here that by default, `splice` will cut up to the end of the array if a second argument, the delete count, isn’t given. We can modify this behavior and only cut 2 items from the starting index.

If we want to cut two items from the array starting at the 5th index:

```javascript
vals.splice(5, 2) // [ 5, 6 ] 
console.log(vals) // [ 0, 1, 2, 3, 4, 7, 8, 9 ]
```

If you want to remove two items from the midpoint of the array:

```javascript
vals.splice( vals.length / 2, 2 ) // [ 5, 6 ]
console.log(vals) // [ 0, 1, 2, 3, 4, 7, 8, 9 ]
```

If you want to remove two items from the `-4` index:

```javascript
vals.splice( -4, 2 ) // [ 6, 7 ]
console.log(vals) // [ 0, 1, 2, 3, 4, 5, 8, 9 ]
```

That’s not all!

`splice` can also take any number of arguments after the delete count. These items will be added to the array, replacing the items that were deleted:

```javascript
vals.splice(5, 2, 'a', 'b') // [ 5, 6 ] 
console.log(vals) // [ 0, 1, 2, 3, 4, 'a', 'b', 7, 8, 9 ]
```

The third and fourth argument above (`'a'` and `'b'`) get added to the original array, replacing `5` and`6`, which are removed and returned as a new array.

### Remembering Which is Which

These two methods have very similar names, which makes it difficult to remember which one does what. Which one modifies the array and which one just returns a shallow copy? Which one do I use to retrieve a segment of an array versus changing a segment of an array?

I wish I had a good pneumonic to help you remember them. But I don’t.

I was able to avoid mixing them up by learning Go, which has a data type called a `slice`. You can also think of the fact that the `splice` method is named after the word splice, which involves interweaving two different strands of ropes into one. When you use `splice` on an array, you’re splicing values into it.

Maybe that will work, but it feels like a bit of a stretch. At any rate, taking some time to study them both should help.

## Implementing Our Own

We’ve discussed both `slice` and `splice` at some length now. Next, let’s turn to how to implement them ourselves. 

### Implementing slice

Our `slice` function needs to take an array and two additional arguments: the `start` and `end` values. By default, the `start` value should be the beginning of the array (so, 0) and the `end` value should be the end of the array. Because that’s just the array’s length, we won’t assign a default value in our parameter list. We should then create and return a new array with the values in this range.

We can start with our function definition:

```javascript
function slice(arr, start = 0, end) {

}
```

The first parameter is the array we want to slice. The second parameter is the starting index for our shallow copy. The third parameter is the end of the range for our slice.

We’re going to use a loop to create our slice, but our loop will be a little different from loops you’re probably used to. We’re going to use two indices instead of just one! I’ll explain why in a minute.

The first case we want to solve for is when we’re just copying an array. We want to do that when someone just passes in an array with no `start` or `end` values. To do that, we need to return an array at the end of our function. And we need to loop through the array that’s passed in:

```javascript
function slice(arr, start = 0, end) {
	let res = []

	for (let i = 0; i < arr.length; i++) {
    	res.push(arr[i])
	}

	return res
}
```

Now if we call `slice(vals)` with our `vals` array from before, we get a copy of the whole array back.

Next, we want to be able to invoke something like `slice(vals, 5)`, like we did above. In that case, we should get the array `[ 5, 6, 7, 8, 9 ]` because our `slice` method will copy the items from index `5` to the end of the array.

All we have to do is change `let i = 0` to `let i = start` in our array:

```javascript
function slice(arr, start = 0, end) {
	let res = []

	for (let i = start; i < arr.length; i++) {
    	res.push(arr[i])
	}

	return res
}
```

Now both the previous example and `slice(vals, 5)` should both work:

```javascript
slice(vals) //[ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
slice(vals, 5) // [ 5, 6, 7, 8, 9 ]
```

The last step here is to make it so `slice(vals, 3, 6)` works, in this case by returning the array `[ 3, 4, 5 ]`. The previous step was about controlling where we start counting for our copy; here, we want to control where we stop counting.

We either want to end at the value passed in for `end` or continue for the whole length of the array. We could use a conditional. A more succinct way to accomplish this is with JavaScript’s logical OR operand (`||`):

```javascript
function slice(arr, start = 0, end) {
	let res = []

	for (let i = start; i < (end || arr.length); i++) {
    res.push(arr[i])
	}

	return res
}
```

Now our loop will count up to the value of `end` or, if `end` is undefined (because a value wasn’t passed in), it’ll count up to the length of the `arr` array that was passed in: 

```javascript
slice(vals) //[ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
slice(vals, 5) // [ 5, 6, 7, 8, 9 ]
slice(vals, 3, 6) // [ 3, 4, 5 ]
```

Easy peasy lemon squeezy.

### Implementing splice

Our `splice` method needs to accept three arguments: the array, a starting index, and the splice length. We'll start at the starting index and make a splice of the passed in array based on the passed in splice length. Our starting index can be positive or negative.If it's negative, we should start counting from the end of the array.

We're not going to try and build all of this at once! Instead, we're going to solve a reduced version of the problem and incrementally ratchet up the complexity. To start, let's create an implementation of `splice` that accepts an array and a starting index and splices the rest of the array from that index.

To start, we need our function signature:

```js
function splice(arr, start) {

}
```

Continuing our theme of implementing these array methods with loops: we're going to use a loop! This time, we'll loop backwards through the array because we want to remove items from the end:

```js
function splice(arr, start) {
  let res = []
  for (let i = arr.length; i > start; i--) {
    res.unshift(arr.pop())
  }
  
  return res
}
```

There's a lot happening here, so let's break it down.

We want to remove items from the end of the array, down to the starting index. This is a lot easier to do than the reverse (starting at the starting index, and removing items to the end). To do it though, we need to loop backwards through the array:

```js
for (let i = array.length; i > start; i--) {

}
```

We're setting our index counter (`i`) to be the length of the array. And we want to keep counting for as long as `i` is greater than the passed in `start` value. With each iteration of the loop, we want to decrement `i` by 1, which is what `i--` does.

Inside our loop, we need to remove items from the end of the original array (`arr`) until we reach that `start` value. The method for removing items from the end of the array is `pop`, so we use that! However, we also need to take the item removed from the end of the array and save it somewhere, so we can return the splice at the end of our function. `pop` returns the removed item, so we immediately pass that into `unshift`, the method for adding items to the beginning of an array. We `pop` from the end of `arr` and `unshift` to the beginning of `res` so that the order in `res` is the same as it was in `arr`.

If we call our `splice` method, we can see that it returns the splice from `vals` and modifies the original `vals` array:

```js
// Returns the spliced segment of the array:
splice(vals, 3) // [3, 4, 5, 6, 7, 8, 9]
// The original array is modified:
console.log(vals) // [0, 1, 2]
```

Why didn't we have to do anything to modify the original `vals` array?

In our `splice` function, we removed items from `arr` and added them to `res`. But we didn't touch the `vals` array. JavaScript passes objects by reference, which means that `arr` is not a new instance of the `vals` array, but a reference to it. `vals` points to the array `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`. When we pass `vals` into `splice` as `arr`, `arr` points to `vals` (which points back to the array). All of this means that any changes we make to `arr` are actually being made on `vals`.

Checking in on our implementation of `splice`: we're able to pass in an array and a starting value and get the splice that we want back while removing it from the original array. Next, we need to make it so `splice` takes a third argument: the length of the splice:

```js
function splice(arr, start, len) {
  let res = []
  for (let i = arr.length; i > start; i--) {
    res.unshift(arr.pop())
  }
  
  return res
}
```

- starting index
- length
- starting index should be able to be negative (in, which case work from the end of the array)


---
## Meta Data

**Domain(s):**
- [[Programming]]
- [[JavaScript]]

**Related Notes:**
- 
