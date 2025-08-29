---
order: -4
icon: globe
label: Online functionality
---

# Working with Online Transaction

The Online Transaction class extends the standard `ITransaction` interface implementation by adding functionality that requires chain API access. This provides enhanced verification capabilities and enables several important online transaction features that aren't available in offline transactions (such as created from TaPoS data, or directly using Protobuf or JSON objects).

## Overview

The Online Transaction class:

- Inherits from the base `ITransaction` class
- Adds online-specific functionality for chain verification
- Provides advanced signing mechanisms for wallets
- Enables security checks for operations to prevent accidental key leaks
- Verifies account existence and authority requirements

## On-Chain Verification

One of the most powerful features of Online Transaction is the ability to perform on-chain verification:

+++ JavaScript

```typescript
import { createHiveChain } from '@hiveio/wax';

// Initialize hive chain interface
const chain = await createHiveChain();

// Initialize an online transaction object
const tx = await chain.createTransaction();

// Declare example operation
const operation = {
  vote_operation: {
    voter: "gtg",
    author: "gtg",
    permlink: "hello-world",
    weight: 2200
  }
};

// Push operation into the transction
tx.pushOperation(operation);

// Perform on-chain verification before broadcasting
try {
  await tx.performOnChainVerification();
  console.log('Transaction passed on-chain verification!');

  // Now safe to broadcast
  // await chain.broadcast(tx);
} catch (error) {
  console.error('Verification failed:', error.message);
}
```

+++ Python

TBA

+++

This verification process includes:

- Scanning for potential private key leaks in memos and comments
- Ensuring referenced accounts exist on the blockchain
- Validating authority changes in account operations

!!!
This verification process is automatically performed **only on online transactions** before broadcasting them.
This way, you won't have to manually perform on-chain verification every time before broadcasting.
!!!

## On-Chain Operation Validation

The Online Transaction uses an internal on-chain operation validator class that performs various security checks:

1. **Private Key Leak Prevention**: Scans operation content (like memos and comments) for accidental inclusion of private keys
2. **Account Existence Verification**: Ensures referenced accounts exist on the blockchain
3. **Authority Modification Safety**: Checks for potentially dangerous authority changes

Example of what this prevents:

+++ JavaScript

```typescript
import { createHiveChain } from '@hiveio/wax';

// Initialize hive chain interface
const chain = await createHiveChain();

// Initialize an online transaction object
const tx = await chain.createTransaction();

// Declare example operation
const operation = {
  transfer_operation: {
    from: "gtg",
    to: "friend",
    amount: chain.hiveCoins(5),
    memo: 'Here is my private key: 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3' // Would be caught!
  }
};

// Push operation into the transction
tx.pushOperation(operation);

// Perform on-chain verification before broadcasting
try {
  // The verification would fail before broadcasting
  await tx.performOnChainVerification(); // Throws error: "Potential private key leak detected!"
} catch (error) {
  console.error('Verification failed:', error.message);
}
```

+++ Python

TBA

+++

## Authority Verification Trace

For debugging or advanced use cases, you can generate a detailed trace of authority verification:

+++ JavaScript

```typescript
// Get detailed authority verification trace
const trace = await tx.generateAuthorityVerificationTrace();

// This trace shows the complete path of authority checks:
console.log('Authority verification complete:', trace.verificationStatus.entryAccepted);
console.log('Authority trace:', trace.rootEntries);
```

+++ Python

TBA

+++

The trace can help understand:

- Which signatures were used
- Which authorities were satisfied
- What authorities are still missing
- The full verification path through nested authorities
