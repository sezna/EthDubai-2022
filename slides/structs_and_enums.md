### Structs and Enums

Note:
Show of hands -- who here knows what I mean when I say "product types" and "sum types"? Or "pi" and "sigma" types? Those are silly words. We want structs and enums, of course. Does anybody know what product and sum types we've seen already?



```rust <!--  data-line-numbers -->
struct NotEnoughFunds { 
  requested: u64, 
  available: u64
}

enum Result<T, E> {
  Ok: T,
  Err: E,
}
```

