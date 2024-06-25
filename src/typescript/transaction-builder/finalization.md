---
order: -3
icon: trophy
label: Finalization
---

# Finalization

When the work with the transaction is ready, you now need to decide what you want to do with it next.

## Building

The simple `build` method returns the proto transaction and also aplies the expiration time:

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

You can also build your transaction into proto form, and add your signature to the internal signatures array (it will also aply the transaction expiration time):

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

// Supplement a transaction with an externally generated signature.
const signedTransaction = tx.build('signature here...');
```

!!!warning Multiple signatures
**Also remember that you can add more than one signature while building your transaction.**
!!!

If you want to build and sign your transaction and return it in proto form, you can use this sample (it will also aply the transaction expiration time):

```typescript
import { createWaxFoundation } from '@hiveio/wax';
import beekeeperFactory from '@hiveio/beekeeper';

// Initialize wax base interface
const wax = await createWaxFoundation();
const bk = await beekeeperFactory();

const session = bk.createSession("salt");
const { wallet } = await session.createWallet("w0");
const publicKey = await wallet.importKey('public key here...');

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

// Build transaction with signature provided.
tx.build(wallet, publicKey);
```

You can also sign the transaction without building it, just replacing the last line of code:

```typescript
// Sign transaction without building it (it will also aply the transaction expiration time).
tx.sign(wallet, publicKey);
```

!!!danger Beekeeper Information
**If you want to sign the transaction, you have to initialize beekeeper library.** If you want to sign the transaction after creating it, using our `TransactionBuilder`, you have to initialize our beekeeper library. Remember to import keys into Beekeeper. It ensures that you can use them securely for transactions and other operations without exposing the raw keys.

Imported key and the one you want to use for signing must be the same!
!!!

### Convertions

At the end you can also just convert your transaction into the Hive API-form JSON:

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

// Convert transaction into the Hive API-form JSON.
tx.toApi();
```
Or you can convert transction to legacy API form by just replacing the last line of code:

```typescript
// Convert transaction into the Hive API-legacy form JSON string
tx.toLegacyApi();
```