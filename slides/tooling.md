### Tooling

----

`forc`


----

Rust SDK

Typescript SDK

----
```rust
async fn mint() {
    let compiled =
        Contract::load_sway_contract("incrementor_contract.bin", salt)
            .unwrap();
    let (provider, wallet) = test_helpers::setup_test_provider_and_wallet().await;
    let id = Contract::deploy(&compiled, &provider, &wallet, TxParameters::default())
        .await
        .unwrap();
    let instance = IncTest::new(id.to_string(), provider, wallet);

```
