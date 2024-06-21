---
order: -1
icon: rocket
label: Initialization
---

# Initializing a Transaction Builder

Once you want to initiliaze `TransactionBuilder` with explicit reference Block data (to satisfy TAPOS) and transaction expiration time:

```typescript
import { createWaxFoundation } from '@hiveio/wax';

const wax = await createWaxFoundation();

// Constructs a new Transaction Builder object with given data.
new wax.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '+30m');
```

Once you have your protobuf transaction ready, you can provide it while constructing:

```typescript
import { createWaxFoundation, transaction } from '@hiveio/wax';

const wax = await createWaxFoundation();

const tx: transaction = {
  ref_block_num: 34559,
  ref_block_prefix: 1271006404,
  expiration: '2021-12-13T11:31:33',
  operations: [],
  extensions: [],
  signatures: []
};

// Constructs a new Transaction Builder object with ready protobuf transaction.
new wax.TransactionBuilder(tx);
```

Once you have your transaction in Hive API-form and you want to convert it to our `TransactionBuilder`:

```typescript
import { createWaxFoundation, transaction } from '@hiveio/wax';

const wax = await createWaxFoundation();

// Stringify the transaction to be able to show the example.
const tx: transaction = JSON.stringify({
  ref_block_num: 34559,
  ref_block_prefix: 1271006404,
  expiration: '2021-12-13T11:31:33',
  operations: [],
  extensions: [],
  signatures: []
});

// Converts Hive API-form transaction in JSON form to our transaction builder.
wax.TransactionBuilder.fromApi(tx);
```

Once you want to have "ready to use" `TransactionBuilder` with reference block data from the remote:

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

// expirationTime is optional in this case.
await chain.getTransactionBuilder();
```