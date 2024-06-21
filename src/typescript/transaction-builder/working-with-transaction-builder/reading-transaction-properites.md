---
order: -3
icon: book
label: Reading properites
---

# Reading transaction properites

The `TransactionBuilder` interface also allows you to read your transaction properties like `sig_digest`, `id`, etc.

```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Initialize wax base interface
const wax = await createWaxFoundation();

// Initialize transaction
const tx = new wax.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '+30m');

// Declare example operation
const operation = JSON.stringify({
  type: 'vote_operation',
  value: {
    voter: 'voter',
    author: 'test-author',
    permlink: 'test-permlink',
    weight: 2200
  }
});

// Push operation into the transction
tx.push(operation);

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
const builtTransaction = tx.build();

// Most transaction properties should be read from the transaction before building it.
tx.id;
tx.sigDigest;
tx.signatureKeys;

// Some transaction properties should be read from the transaction after building it.
builtTransaction.signatures;
builtTransaction.expiration;
builtTransaction.operations;
```