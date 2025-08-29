---
order: -5
icon: ../../static/peakvault.svg
---

# PeakVault

Wax signer library extending transaction signing possibilities by a 3rd party Web-only extension - Peak Vault

## Install package

```bash
pnpm add @hiveio/wax-signers-peakvault
```

## Prerequisites

- Configured [Peak Vault browser extension](https://vault.peakd.com/peakvault/releases.html) with imported keys

## Usage

```typescript
import { createHiveChain } from "@hiveio/wax";
import PeakVaultProvider from "@hiveio/wax-signers-peakvault";

const chain = await createHiveChain();

const provider = PeakVaultProvider.for("myaccount", "active");

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
