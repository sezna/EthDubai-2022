### Macros

----

1. Procedural (`#[some_macro_thing(yes)]`)
1. Derive (`#[derive(Clone)]`)
1. Declarative (`assert!`)

----

#### Derive
```
#[derive(Getter)]
let mut balance = 0;
```

----

#### Procedural
```rust
parse_html! {
  <h1> literally anything goes in proc macros </h1>
}
```

----

#### Declarative
```rust
assert_eq!(alexs_balance, 0);
```
