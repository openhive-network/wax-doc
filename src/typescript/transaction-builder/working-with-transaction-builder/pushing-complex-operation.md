---
order: -3
icon: graph
label: Complex operation
---

# Adding complex operations

If you want to work with `TransactionBuilder` in more complex way, it is recommendet to initialize it from hive chain interface. It allows you to avoid complexity of your work.

Below is an example of fully building more complex transaction using the `TransactionBuilder` interface and our `useBuilder` functionality.

```typescript
import { createHiveChain, WitnessSetPropertiesBuilder } from '@hiveio/wax';

// Initialize chain
const chain = await createHiveChain();

// Initialize transaction
const tx = await chain.getTransactionBuilder();

// Build operation
tx.useBuilder(WitnessSetPropertiesBuilder, builder => {
  builder.setUrl('https://example.com')
}, 'owner', 'STM...');

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
const builtTransaction = tx.build();
```
The `useBuilder` method allows for simple construction of an operation. It takes the following parameters:
- The constructor of the builder class you want to use,
- An arrow function, inside which you can make use of all the methods available within the given builder,
- Other arguments specific to the given builder.

The `useBuilder` method returns an instance of `TransactionBuilder`, on which you can later perform operations related to the transaction.

More complex information about `useBuilder` are presented in subsequent chapters.