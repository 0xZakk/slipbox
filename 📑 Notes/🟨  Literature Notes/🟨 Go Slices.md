- **Type:** #[[__ 🟨 Literature Note]]  | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- While arrays in Go are powerful, most developers tend to use Slices instead. Slices are more powerful than Arrays because they can change dynamically (they can increase and decrease in length as needed).
- The way you create a Slice is very similar to the way you create an Array (you just commit the length):
- ```javascript
var a []int```
- The above snippet creates a Slice, `a` for storing `int` values.
- You can also initialize Slices with values:
- ```javascript
primes := []int{2, 3, 5, 7, 11, 13}```
- The above creates a slice of numbers and adds 6 numbers into it
- You can get the length of a Slice by using the `len()` function:
- ```javascript
length := len(a)```
- You can add an item to a Slice by using the `append()` function:
- ```javascript
a = append(a, 5)```
- The `append()` method can take multiple values as arguments to add to the slice:
- ```javascript
a = append(a, 1, 2, 3, 4, 5)```
- `append()` returns a new slice containing all the elements of the original slice and all the appended items
