---
order: -4
icon: ../../static/keychain.svg
---

# Keychain

Wax signer library extending transaction signing possibilities by a 3rd party Web-only extension - Keychain

## Install package

```bash
pnpm add @hiveio/wax-signers-keychain
```

## Prerequisites

- Configured [Keychain browser extension](https://hive-keychain.com/) with imported keys

## Usage

```typescript
import { createHiveChain } from "@hiveio/wax";
import KeychainProvider from "@hiveio/wax-signers-keychain";

const chain = await createHiveChain();

const provider = KeychainProvider.for("myaccount", "active");

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
await tx.sign(provider);

// broadcast the transaction
await chain.broadcast(tx);
```
