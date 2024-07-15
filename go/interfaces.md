## Interfaces

- Keep interfaces **small**, it should only define the minimal behavior necessary
- Interfaces should have no knowledge of the implementation that satisfies them

```go
type Person interface {
  Name() string
  Age() int
  IsPolitician() bool // interface should not have this method
}
```

- Interfaces are **NOT** classes, no constructors, destructors

## References

- [BEST PRACTICES FOR INTERFACES IN GO
  ](https://blog.boot.dev/golang/golang-interfaces/)
