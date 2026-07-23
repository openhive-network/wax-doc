---
order: -1
icon: ../../static/beekeeper.svg
---

# Beekeeper

Wax signer library extending transaction signing possibilities by a safe wallet - Beekeeper

## Install package

+++ JavaScript

[!ref icon="../../static/npm.svg" target="_blank" text="View **Beekeeper signer** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-signers-beekeeper)

```bash
pnpm add @hiveio/wax-signers-beekeeper
```

+++ Python

```bash
pip install beekeepy --index-url https://gitlab.syncad.com/api/v4/projects/434/packages/pypi/simple
```

+++ Rust

[!ref icon="../../static/crates_io.png" target="_blank" text="View **Beekeeper signer** crate on crates.io"](https://crates.io/crates/hiveio-wax-signers-beekeeper)

```bash
cargo add hiveio-wax-signers-beekeeper
```

> The crate is imported as `wax_signers_beekeeper` in code, e.g.: `use wax_signers_beekeeper::BeekeeperSignatureProvider;`

+++

## Usage

+++ JavaScript

```typescript
import { createHiveChain } from "@hiveio/wax";
import BeekeeperProvider from "@hiveio/wax-signers-beekeeper";

const chain = await createHiveChain();

const provider = BeekeeperProvider.for(myWallet, "myaccount", "active", chain);

// Create a transaction using the Wax Hive chain instance
const tx = await chain.createTransaction();

// Perform some operations, e.g. push the vote operation:
tx.pushOperation({
  vote_operation: {
    voter: "alice",
    author: "bob",
    permlink: "example-post",
    weight: 10000
  }
});

// Wait for the keychain to sign the transaction
 await provider.signTransaction(tx);

// broadcast the transaction
await chain.broadcast(tx);
```

+++ Python

:::code source="../../static/snippets/src/python/transaction/signers/sign_transaction_by_beekeeper.py" language="python" :::

+++ Rust

```rust
use beekeeper::api::BeekeeperApi;
use beekeeper::options::BeekeeperOptions;
use wax::prelude::*;
use wax_signers_beekeeper::BeekeeperSignatureProvider;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    let chain = create_hive_chain(None)?;

    // Open an in-memory Beekeeper wallet and import your private key
    let api = BeekeeperApi::new(BeekeeperOptions::new("my-storage").in_memory(true));
    let session = api.create_session()?;
    let mut wallet = session.create_wallet("my-wallet", "my-password")?.wallet;
    let public_key = wallet.import_key("your-private-key")?;

    // Wrap the unlocked wallet in a Wax signature provider
    let provider = BeekeeperSignatureProvider::new(wallet);

    // Create a transaction using the Wax Hive chain instance
    let mut tx = chain.create_transaction(None).await?;

    // Perform some operations, e.g. push the vote operation:
    tx.push_operation(chain.create_operation(Value::VoteOperation(Vote {
        voter: "alice".into(),
        author: "bob".into(),
        permlink: "example-post".into(),
        weight: 10000,
    })));

    // Sign the transaction
    tx.sign(&provider, &public_key)?;

    // Broadcast the transaction
    chain.broadcast(&tx).await?;

    Ok(())
}
```

+++
