---
order: -5
icon: flame
label: Example usage
---

# Example Transaction Builder usage

Once you know all the `TransactionBuilder` functionality, let's look at an example of complete usage.

```typescript
import { createHiveChain, ReplyBuilder, BroadcastTransactionRequest } from '@hiveio/wax';
import beekeeperFactory from '@hiveio/beekeeper';

import fs from 'node:fs';

// Initialize chain
const chain = await createHiveChain();

// Initialize beekeeper
const bk = await beekeeperFactory();

// Create a session
const session = bk.createSession('salt');

// Create a wallet
const { wallet } = await session.createWallet('w0');

// Import public keys
const publicKey = await wallet.importKey('public key here...');
const anotherPublicKey = await wallet.importKey('another public key here...');

// Create a transaction
const tx = await chain.getTransactionBuilder();

// Use the ReplyBuilder to create a reply operation
tx.useBuilder(ReplyBuilder, builder => {
    builder
      .addBeneficiaries({ account: 'test', weight: 40 })
      .pushTags('tag')
      .setDescription('description');
  },
  'parent_author',
  'parent_permlink',
  'author',
  'body'
);

// Convert the transaction into the Hive API-form JSON
const apiTransaction = tx.toApi();

// Save the transaction to a file
fs.writeFileSync('transaction.json', apiTransaction);

// Apply the transaction in the API form into transaction builder interface
const txFromApi = chain.TransactionBuilder.fromApi(apiTransaction);

// Build the transaction with signature provided
const txSigned = txFromApi.build(wallet, publicKey);

// Save the signed transaction to a file
fs.writeFileSync('transaction-signed.json', JSON.stringify(txSigned));

// Apply the already signed transaction in the API form into transaction builder interface
const txSignedFromApi = chain.TransactionBuilder.fromApi(txFromApi);

// Multi sign the transaction with another public key
txSignedFromApi.build(wallet, anotherPublicKey);

// Save the multi signed transaction to a file
fs.writeFileSync('transaction-signed-multi.json', JSON.stringify(txSignedFromApi));

// Broadcast the transaction
const txBroadcasted = new BroadcastTransactionRequest(txSignedFromApi);

// Save the broadcasted transaction to a file
fs.writeFileSync('transaction-broadcasted.json', JSON.stringify(txBroadcasted));
```