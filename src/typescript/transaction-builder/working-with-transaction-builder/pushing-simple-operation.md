---
order: -2
icon: milestone
label: Simple operation
---

# Pushing simple operation

If your case is to perform simple actions on your transaction or create a new transaction, you can use initialization with the wax base interface.

Below is an example of fully building a simple transaction using the basic `TransactionBuilder` interface.

```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Initialize wax base interface
const wax = await createWaxFoundation();

// Initialize transaction
const tx = new wax.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

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
```
