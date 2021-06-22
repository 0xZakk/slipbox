# 🟨 Declaring variables in Go

Go provides many ways of declaring variables, each with their own trade-offs.

## Variable Declaration

The first way you can declare a variable is with the `var` keyword. When using the `var` keyword, you need to provide a name for the variable and assign it a type:

```go
var name string
var favoriteNumber int
```

## Variable Declaration and Assignment

You can also assign a value to a variable when it's declared using the assignment operator (`=`). If you do this, you can still provide a type declaration or you can leave it out and the Go compiler will guess the type.

```go
var name = "Zakk"
var favoriteNumber = 5
```

## Short Assignment

Most Go programmers use short assignment to declare variables. This creates the variable, assigns a value, and sets the type all in a succinct statement.

```go
name := "Zakk"
favoriteNumber := 5
```

## Type Conversion

Type conversion has to be handled explicitly in Go - it cannot be done implicitly and the Go compiler will not coerce variables for you. So, for instance, the `math.Abs()` method expects a `Float64` type as an argument. If your variable is any other type, the compiler will throw an error. This is the case even for other number types.

---
[[__ 🟨 Literature Note]]

Source:  [[🟦 Go In Action (Preview)]]
Domain(s):
- #Go

