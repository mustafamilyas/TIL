# Variadic Function & Spread Operator

Variadic function is a function that accepts a variable number of arguments. In JavaScript, you can use the rest parameter syntax to create a variadic function.

```javascript
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3)); // 6

console.log(sum(1, 2, 3, 4, 5)); // 15
```

On the example above, the `sum` function accepts a variable number of arguments. The `numbers` parameter will be an array that contains all the arguments passed to the function.

In Go, you can create a variadic function by using the `...` syntax. The `...` syntax is used to indicate that the function accepts a variable number of arguments.

```go
package main

import "fmt"

func sum(numbers ...int) int {
    total := 0
    for _, num := range numbers {
        total += num
    }
    return total
}

func sendEmail(to string, cc ...string) {
    fmt.Println("To:", to)
    fmt.Println("CC:", cc)
}

func main() {
    fmt.Println(sum(1, 2, 3)) // 6
    fmt.Println(sum(1, 2, 3, 4, 5)) // 15

    sendEmail("ilyas@gmail.com", "test@gmail.com", "mustafa@gmail.com")
}
```

On the flip side, you can use the spread operator to pass an array / slice as arguments to a function.

```javascript
function sum(a, b, c) {
  return a + b + c;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers)); // 6
```

```go
package main

import "fmt"

func sum(a, b, c int) int {
    return a + b + c
}

func main() {
    numbers := []int{1, 2, 3}
    fmt.Println(sum(numbers...)) // 6
}
```

Notice the `...` syntax on the `sum` function call. It is used to spread the `numbers` array into individual arguments. In go, you put the spread operator `...` **after** the slice variable name. In JavaScript, you put the spread operator `...` **before** the array variable name.
