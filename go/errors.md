# Errors

In go languange, errors are values. Instead of throwing an exception likes in other languages (javascript), go uses error values to indicate an exceptional condition.

```javascript
async function main() {
  try {
    const result = await getUser();
  } catch (error) {
    console.error(error);
  }
}
```

```go
package main

import (
    "errors"
    "fmt"
)

func main() {
    users, err := getUser()
    if err != nil {
        fmt.Println(err)
    }
}

func getUser() ([]string, error) {
    return nil, errors.New("failed to get user")
}
```

The `errors.New` function creates a new error with the given message. The `fmt.Println` function prints the error message.

## Custom Errors

You can create custom errors by implementing the `Error()` method on a struct.

```go

package main

import (
    "fmt"
)

type NetworkError struct {
    StatusCode int
    Message    string
}

func (e NetworkError) Error() string {
    return fmt.Sprintf("Network error: %s (status code: %d)", e.Message, e.StatusCode)
}

func getUser() ([]string, error) {
    return nil, NetworkError{StatusCode: 404, Message: "failed to get user"}
}

func main() {
    users, err := getUser()
    if err != nil {
        fmt.Println(err)
    }
}
```
