# 🟨 Conditional statements in Go

In Go, you use the `if` keyword to create a conditional statement. The condition itself is not wrapped in parentheses like it is in other programming languages. The block of code to be executed if a condition is met is wrapped in curly braces:

```go
if name == "Zakk" {
  fmt.Println("Hello Zakk")
}
```

You can expand on this notation to include additional conditions using `else` and `else if`. If you are adding an explicit condition, you once again do not use parentheses:

```go
func main() {
	age := 21
	if age >= 21 {
		fmt.Println("You may enter")
	} else if age == 20 {
		fmt.Println("Come back in a few months")
	} else {
		fmt.Println("You must be 21 or older to enter")
	}
}
```


---
[[__ 🟨 Literature Note]]

Source: [[🟦 Go In Action (Preview)]]
Domain(s):
- [[Arrays and Slices in Go]]


