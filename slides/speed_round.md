### Speed round


#### Ifs are expressions
```rust
let civilian_time = if time.hours > 12 {
    Time { 
      hours: time.hours - 12, 
      minutes: time.minutes 
    }
  } else {
    time
  };
```


#### Unchecked Arithmetic

```rust
arithmetic: wrapping {
   0xff_fff_fffu32 + 1 == 0
}
```

Note: we use the canonical names of the arithmetic types instead of the more vague "unchecked" term. Math will panic if it overflows by default. 


#### Sweet underscore syntax
```rust
arithmetic: wrapping {
   0xff_fff_fffu32 + 1 == 0
}
```


#### Matches are Expressions
```rust
let centimeters = match unit {
  Unit::Centimeters => x,
  Unit::Decimeters => x * 10,
  Unit::Meters => x * 1_000,
  Unit::Kilometers => x * 100_000,
  _ => return Err(UnknownUnit)
}
```

Note:
Note that this is a match as an expression, and note exhaustive errors
