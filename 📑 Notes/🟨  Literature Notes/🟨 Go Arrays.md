- **Type:** #[[__ 🟨 Literature Note]] | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- Go offers two common forms of lists: arrays and slices. They are similar in many ways (for instance, in how you access data), but have some key differences.
- When you define an array in Go, you have to declare in advance the size of the array. This is different from how arrays are commonly used in other languages like JavaScript and Python.
- This is how you create an array in Go:
- ```javascript
var a [10]int```
- The above creates an array, `a` for storing up to 10 `int` values.
- This is how you initialize an array with values:
- ```javascript
primes := [6]int{2, 3, 5, 7, 11, 13}```
- The above code creates an array, `primes`, for storing 6 numbers, `{2, 3, 5, 7, 11, 13}`
- It's important to note that you have to declare the size of an array when it's created and that you cannot change the size of the array after creation.
- You can have the Go compiler figure out the length of the array for you:
- ```javascript
primes := [...]int{2, 3, 5, 7, 11, 13}```
- If you leave the brackets empty, then you'll create a slice
