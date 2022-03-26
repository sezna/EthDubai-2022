
### State Variables


```solidity
pragma solidity >=0.4.0 <0.9.0;
contract SimpleStorage {
    uint storedData; // State variable
    // ...
}
```

Note:
Let's dive right in. Solidity begins its documentation by introducing us to some basic contract storage. 
This pragma is handled in our toml file, similarly to how Rust configures via Cargo.toml.


```solidity
pragma solidity >=0.4.0 <0.9.0;
contract SimpleStorage {
    uint storedData; // State variable
    // ...
}
```
```rust
contract;

storage {
  stored_data: u64,
}

#[storage(read, write)]
fn contract_function() { 
  storage.stored_data = storage.stored_data + 1;
}
```

Note:
We have a few reasons behind this design decision. For one, remember that tweet? Have you ever prefixed a variable with something to denote that it is indeed a state variable?
We see no reason why that shouldn't be a language pattern, so, to access state variables, we use the `storage` keyword.
If you have been following Sway for a while, you'll notice we now use the `storage` keyword to denote storage access. 
Additionally, you'll notice we have an annotation system similar to rust. This is extensible. We use it to provide compile-time checks of function impurity and state access patterns and anti-patterns.
