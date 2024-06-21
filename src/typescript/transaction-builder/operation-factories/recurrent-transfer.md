---
order: -2
icon: file-moved
---

# Using RecurrentTransfer

The `RecurrentTransferBuilder` allows for initiating, modifying, and removing recurrent transfers on the Hive blockchain.

## Creating a New Recurrent Transfer

```typescript
import { createHiveChain, RecurrentTransferBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const from = "sender-account";
const to = "recipient-account";
const amount = chain.hive(10000); // 100.000 HIVE
const memo = "Monthly subscription";
const recurrence = 24; // every day
const executions = 30; // for 30 days

tx.useBuilder(RecurrentTransferBuilder, () => {}, from, to, amount, memo, recurrence, executions);

tx.build(); // builds the operation ready for broadcasting
```

## Add Pair Id

In this example we add pair id to recurrent transfer, using `RecurrentTransferPairIdBuilder` which inherits from `RecurrentTransferBuilder`

```typescript
import { createHiveChain, RecurrentTransferPairIdBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const from = "sender-account";
const to = "recipient-account";
const pairId = 12345;
const amount = chain.hive(10000); // 100.000 HIVE
const memo = "Monthly subscription";

// Use this time just for example default values for recurrence and executions which is 24 for recurrence and 2 for executions.
tx.useBuilder(RecurrentTransferPairIdBuilder, builder => {
    builder.generateRemoval();
}, from, to, pairId, amount, memo);

tx.build(); // builds the operation ready for broadcasting
```

## Generate Removal Using RecurrentTransferBuilder

Generate removal removes recurrent transfer with the previously set pair id

```typescript
import { createHiveChain, RecurrentTransferPairIdBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const from = "sender-account";
const to = "recipient-account";
const pairId = 12345;
const amount = chain.hive(10000); // 100.000 HIVE
const memo = "Monthly subscription";

// Use this time just for example default values for recurrence and executions which is 24 for recurrence and 2 for executions.
tx.useBuilder(RecurrentTransferPairIdBuilder, builder => {
    builder.generateRemoval();
}, from, to, pairId, amount, memo);

tx.build(); // builds the operation ready for broadcasting
```
