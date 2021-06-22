- **Type:** #[[__ 🟨 Literature Note]] | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- One of the key features of Slices in Go is that you can select parts of them using slicing syntax (similar to Python).
- Given the following slice:
- ```javascript
nums := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}```
- You can retrieve a subset of this slice by using the range notation:
- ```javascript
favoriteNums := nums[3:5]```
- The first number provided in the range is the starting index of your range and the second number is the ending index (unlike in other programming languages where the second number is the length of the slice).
- The slice syntax has a third argument: the capacity of the resulting slice
- ```javascript
favoriteNums := nums[3:5:5]```
- Here, the first and second numbers determine the range and the third value determines the capacity.
- **Important:** See [[🟨 Determining Slice Capacity in Go]]
