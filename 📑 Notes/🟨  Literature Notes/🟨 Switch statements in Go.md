- **Type:** #[[__ 🟨 Literature Note]] | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- When used appropriately, the `switch` statement can replace a complicated `if`/`else` structure and make complicated conditionals easier to read and understand. 
- Switch statements in Go behave much like they do in other programming languages. You pass in an argument and it matches with a `case`. You can also set a `default`.
- ```javascript
switch argument {
  case "0":
    fmt.Println("Zero!")
  case "1":
    fmt.Println("One!")
  case "2", "3", "4":
    fmt.Println("2 or 3 or 4")
    fallthrough 
  default:
    fmt.Println("Value:", argument)
}```
    - You use `switch <argument>` to build a conditional off of the statement (`<argument>`). Then you provide the cases you'd like to test against.
    - A matching case uses the notation `case <value>:` where `<value>` is the value you'd like to test `<argument>` against. You follow each case with a code block.
    - You can have as many cases to match against as you'd like
    - You can also match against multiple values in a single case test by providing a list of matches: `case "2", "3", "4":`
    - `fallthrough` tells Go to continue (fall through) the remaining branches after executing this branch. In this case, if the value of `argument` is `"2"`, `"3"`, or `"4"`, then this case will match and Go will print `"2 or 3 or 4"`. Go will then continue on to the next case, which is the `default`.
    - You can also provide default cases with `default:`
- There is a second way that you can use the `switch` structure and that is without an expression:
- ```javascript
switch {
  case value == 0:
	fmt.Println("Zero!")
  case value > 0:
	fmt.Println("Positive integer")
  case value < 0:
	fmt.Println("Negative integer")
  default:
	fmt.Println("This should not happen:", value)
}```
    - In this form, instead of comparing the expression after `switch` to the value after each `case`, the expression of each `case` statement is evaluated
    - This increases the overall flexibility of the `switch` structure
