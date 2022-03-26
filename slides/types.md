            ### Types
Note:
Our type system is essentially the same as Rust's, with a few differences:

----

### Primitive Types
1. Unsigned Integers
1. Booleans
1. Static-length strings
1. 32-byte values
1. Single-byte values
1. The unit type

Note: 
We mainly just support the primitive types that Solidity cares about, and are common in smart contracts.

----

### Generics and Traits

```rust
contract;
trait Foo<T, E>
  where T: Bar + Baz,
        E: Quux {
      [ ... ]
  }
```

Note: 
We do fully support generic types and traits in the same way Rust does.
All of the solidity address, contract, and hash types are wrapper types around byte32 with their own APIs in the standard library.
addresses are 32 bytes, which is what addresses are going to be very soon due to "address extension" changes

Bytes and addresses can be declared with literal syntax.

----

```rust
let x: byte32 =
 0xAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAFAF; 

let y: byte = 0xAF;

let z: byte = 0b10101010;
```
----

### Discriminated Unions

```rust
enum Sale {
  Product: Product,
  Service: Service,
}

struct Product {
  sku: str[8],
  price: u64,
}

struct Service {
  name: str[15],
  hourly_rate: u64,
}
```


Note: We also support discriminated union types, where the variants of the enumeration contain different values. 
