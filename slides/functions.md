### Functions


```solidity
contract SimpleAuction {
    function bid() public payable { // Function
        // ...
    }
}

// Helper function defined outside of a contract
function helper(uint x) pure returns (uint) {
    return x * 2;
}

```
Note:
A function in Solidity looks like this. Let's take a look at what this is doing -- we are creating an auction contract with some bid method that is payable. 
We also have a helper pure function which multiplies a number by 2.


```rust
contract;

abi SimpleAuction {
  fn bid();
}

impl SimpleAuction for Contract {
  fn bid() {
    ..
  }
}

fn helper(x: u64) -> u64 {
  x * 2
}

```

Note:
Now, let's take a look at the equivalent Sway code.
There are three examples of functions here. Let's take a look at the function called `helper`. (point out: rust syntax, type annotation, return type, implicit return)

We have replaced the Solidity inheritence/constructor based system with a trait based system. The order of constructors and inheritence-related implicit behavior often leads to difficulty in auditing and vulnerabilities. With a trait (or if you know Haskell, typeclass)-based system, implicit control flow is minimized.
The `abi` keyword denotes what is essentially a trait -- a type class for you Haskellers, an interface for you Java beans. This defines an interface that can be imported 
into other Sway programs to either implement contracts with the same interface, or, to interact with contracts. But we will get to that in a bit. For now, just know that the `abi` 
keyword defines a special kind of trait, typeclass, what-have-you, that can be implemented on contracts themselves.

Functions are pure by default.


```solidity
contract Purchase {
    address public seller;

    modifier onlySeller() { // Modifier
        require(
          msg.sender == seller,
          "Only seller can call this."
        );
        _;
    }

    // Modifier usage
    function abort() public view onlySeller { 
        // ...
    }
}
```

Note:
Because modifier behavior can be accomplished with function composition and traits, we chose not to use function modifiers.
This eliminates a lot of organizational and security issues related to their opaqueness and redirects. Additionally, when
an `_` is used to denote "paste the body of the modified function here", it is not optimized properly. 

We also use an `assert` that is more similar to Rust's assert instead of require, but very similar.


```rust
contract;

let seller: Address = Address(
  0xDEADBEEF...
);

abi Purchase {
  view fn abort();
} 

impl Purchase for Contract {
  view fn abort() {
    assert(context.caller_id == seller);
    abort_inner()
  }
}
```

Note:
view functions, constant values, deploy-time values, macros, assert_eq, modifiers can be solved with 
function composition and have nothing to do with the blockchain therefore we didn't keep them
