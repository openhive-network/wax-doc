---
order: -2
icon: credit-card
---

# HB Auth

Wax signer library extending transaction signing possibilities by a 3rd party Web-only extension - hb-auth.

## Install package

[!ref icon="../../static/npm.svg" target="_blank" text="View **HB Auth signer** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-hb-auth)

```bash
pnpm add @hiveio/wax-signers-hb-auth
```

## Usage

```typescript
import { createHiveChain } from "@hiveio/wax";
import HBAuthProvider from "@hiveio/wax-signers-hb-auth";

const chain = await createHiveChain();

const provider = HBAuthProvider.for(hbAuthClient, "gtg", "posting");

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
