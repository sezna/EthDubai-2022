### Errors


```solidity
error NotEnoughFunds(uint requested, uint available);

contract Token {
    mapping(address => uint) balances;
    function transfer(address to, uint amount) public {
        uint balance = balances[msg.sender];
        if (balance < amount)
            revert NotEnoughFunds(amount, balance);
        balances[msg.sender] -= amount;
        balances[to] += amount;
        // ...
    }
}
```

Note:
Here's another cool thing solidity does -- reverts in your control flow. We want to keep that. Do one thing well, revert otherwise. That's the smart contract way, right?


```rust
contract;
use std::chain::Address;

struct NotEnoughFunds { 
  requested: u64, 
  available: u64
}

impl Token for Contract {
  naughty fn transfer(to: Address, amount: u64) {
        if contract.balances[msg.sender] < amount { 
          revert(NotEnoughFunds { requested: amount, available: contract.balances[msg.sender] });
        }
        contract.balances[msg.sender] -= amount;
        contract.balances[to] += amount;
        // ...
  }
}
```

Note:
note on revert is like panic! via Revertable trait which controls how it shows up in a revert
Should you want to revert, you don't need a return type since that aborts the control flow. However, you are perfectly free to also do this:


```rust
contract;
use std::chain::{balance, Address};

struct NotEnoughFunds { 
  requested: u64, 
  available: u64
}

impl Token for Contract {
  #[state(read, write)]
  fn transfer(to: Address, amount: u64) 
    -> Result<(), NotEnoughFunds> {
        if balance() < amount { 
          return Err(NotEnoughFunds { 
           requested: amount,
           available: storage.balances[msg.sender] 
          });
        }
        storage.balances[msg.sender] -= amount;
        storage.balances[to] += amount;
        // ...
  }
}
```

Note:
