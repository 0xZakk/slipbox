- **Type:** #[[__ 🟨 Literature Note]] | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- The Go slice syntax has three arguments:
    - The starting index
    - The ending index
    - The capacity of the new slice
- So if we have the following slice:
- ```javascript
nums := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}```
- We can create the slice `[]int{3, 4, 5}` like this:
- ```javascript
nums[2:5:5]```
- Where `2` is the starting index, the first `5` is the ending index, and the second `5` is the capacity of the new slice
- However, the capacity is determined by subtracting the starting index from the third argument. So in the example above, `2 - 5` is what gives us the slice capacity (`3`)
