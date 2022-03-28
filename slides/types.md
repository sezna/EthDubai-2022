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

### Discriminated Unions (Sum Types)

```rust
enum Sale {
  Product: Product,
  Service: Service,
}

struct Product {
  id: u64,
  price: u64,
}

struct Service {
  name: str[15],
  hourly_rate: u64,
}
```


Note: We also support discriminated union types, where the variants of the enumeration contain different values. 

----
```rust
let my_variable = match {
  1 => { do something },
  2 => { do something },
};

```

Note:
TODO get real err msg for above

Having expressive types unlocks additional analysis! 
The more of your problem you lift into the type system, the more gets solved at compile time and the less runtime errors, aka vulnerabilities, your software will have.

For example, exhaustivity checking on match expressions is entirely possible at compile time. It does require some work on the compiler's side, and it requires a good type system. But we have put in the work and the type system is sufficient. 

----

# Ecrecover


Note: How many of you are familiar with ecrecover? Are you all familiar with what happens in the case that ecrecover fails? <ask>


----


`0x0000000000000000000000000000000000000000000000000000000000000000`


Note:
You get a buch of zeroes. This is generally considered an anti pattern known as "sentinal values" or "magic numbers".  A value within the range of the function's expected output is a sentinal that represents some other meaning. This is not secure. The programmer must remember to check for all sentinal values every time this function is used (potential vulnerability); sentinal values, especially addresses, can theoretically be hijacked (vulnerability), and there are correctness issues when sentinal values can conflict with valid results.


----

```rust
enum Result<T, E> {
  Ok: T,
  Err: E,
}

```

Sum types, a.k.a. enums, solve all of this. The compiler enforces that both cases are handled appropriately. It is proven at compile time that none of these vulnerabilities will happen. We just solved three vulnerabilities, isn't that great? And, the entire address space can now be returned by this function with no concern for collision. 
