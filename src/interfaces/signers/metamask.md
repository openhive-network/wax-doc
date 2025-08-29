---
order: -3
icon: ../../static/metamask.svg
---

# MetaMask

Wax signer library extending transaction signing possibilities by the Hive Wallet - a 3rd party Web-only MetaMask extension snap

Please read the [Knowledge Base](https://github.com/openhive-network/metamask-snap/wiki/KB#on-chain-usage)

## Install package

```bash
pnpm add @hiveio/wax-signers-metamask
```

## Prerequisites

- Configured MetaMask (Flask) wallet according to [the tutorial](https://youtu.be/zKT1GXO6G-0)

## Usage

```typescript
import { createHiveChain } from "@hiveio/wax";
import MetaMaskProvider from "@hiveio/wax-signers-metamask";

const chain = await createHiveChain();

const provider = MetaMaskProvider.for(0);

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
