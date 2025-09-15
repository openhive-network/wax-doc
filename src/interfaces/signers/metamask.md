---
order: -3
icon: ../../static/metamask.svg
---

# MetaMask

Wax signer library extending transaction signing possibilities by the Hive Wallet - a 3rd party Web-only MetaMask extension snap

!!!success
We were able to leverage the MetaMask Snap SDK to create a Hive-compatible signer that works seamlessly with MetaMask. This integration allows users to manage their Hive accounts and sign transactions directly within the MetaMask interface, providing a familiar and secure experience for those already using MetaMask for Ethereum and other EVM-compatible chains: [Official Hive Wallet Snap](https://snaps.metamask.io/snap/npm/hiveio/metamask-snap/)
!!!

Please read the [Knowledge Base](https://github.com/openhive-network/metamask-snap/wiki/KB#on-chain-usage) for more details on how to use the Hive Wallet Snap. You can also check out our official dApp - [Hive Bridge](https://auth.openhive.network).

## Install package

[!ref icon="../../static/npm.svg" target="_blank" text="View **MetaMask signer** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-signers-metamask)

```bash
pnpm add @hiveio/wax-signers-metamask
```

## Prerequisites

- Configured MetaMask wallet according to [the tutorial](https://youtu.be/zKT1GXO6G-0)

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
 await provider.signTransaction(tx);

// broadcast the transaction
await chain.broadcast(tx);
```
