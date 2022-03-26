### Example Contract

```rust
contract;
let mut balance = 0;
abi UnauthenticatedMoneyHole {
   fn deposit();
   fn get_balance() -> u64;
}

impl UnauthenticatedMoneyHole for Contract {
  fn deposit() {
    contract.balance += msg.value;
  }
  fn get_balance() -> u64 {
    contract.balance
  }
}
```

----

```rust
use moneyhole::UnauthenticatedMoneyHole;
let caller = contract_caller(
                contract_address,
                UnauthenticatedMoneyHole
             );

// Deposit 0 coins.
caller.deposit(CallParameters::default());
```
