- **Type:** #[[__ 🟨 Literature Note]] | [[Arrays and Slices in Go]]
- **Source:** [[🟦 Go In Action (Preview)]]
- Functions in Go are defined with the `func` keyword. They are given a name, an optional list of parameters, followed by a block - just like in other programming languages:
- ```javascript
func sayHello(name string) {
  fmt.Println("Hello, ", name)
}```
- The list of parameters is optional for functions:
- ```javascript
func sayHello() {
	fmt.Println("Hello, World")
}```
- If you do provide a parameter list, you must include the type declarations for each argument:
- ```javascript
func sayHello(name string, age int) {
	fmt.Println("Hello, ", name, ". You are ", age, " years old.")
}```
- You also have to declare types for the return values for a function. Note that a function in Go can return multiple values
- ```javascript
package main

import "fmt"
import "strconv"

func sayHello(name string, age int) string {
	s := strconv.Itoa(age)
	message := "Hello, " + name + ". You are " + s + " years old."
	return message
}

func main() {
	message := sayHello("Zakk", 29)
	fmt.Println(message)
}```
    - Here we have the type declared for the return value (`string`) after the list of parameters
    - Note that in this case, in order to return a string, we have to convert `age` from an `int` into a `string` type
