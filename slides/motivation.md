
# What is Sway?



Note:
  Sway was motivated by Solidity and Rust. We believe in the Rust philosophy of language design,
  and we want to combine that with the ergonomic first-class blockchain support that Solidity brings to the table. 

----

![](https://raw.githubusercontent.com/sezna/EthDubai-2022/master/images/native_asset_vuln.png)


Note:
TODO get image from chromium for above
  The programming model is similar to Ethereum, although we allow for multiple native assets. This removes the error class of bugs in your token code entirely.


----

https://www.chromium.org/Home/chromium-security/memory-safety/


Note:
A lot of people wonder why we don't have specific features of Rust, like async/await or Send/Sync, if we want to be like Rust. Our goal is not to reimplement the language. It is to take the philosophy and apply it to the smart contract space. 

< chromium anecdote >

Memory safety bugs are not nearly as much of an issue in the smart contract world. But, we want to do what Rust did -- eliminate entire classes of bugs by virtue of design choices and static analysis. Native assets are a part of that, as are our storage paradigms, tooling story, and everything else.

