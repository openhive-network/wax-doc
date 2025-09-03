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

TBA

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

TBA

+++
