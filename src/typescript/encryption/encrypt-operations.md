---
order: -2
icon: fiscal-host
---

# Encrypt operations

Wax library provides a simple interface for operations encryption withing transaction using Transaction Builder interface.

## Operations That Can Be Encrypted

Currently, the following operations can be encrypted using the `@hiveio/wax` library:

- [!badge variant="info" text="comment"] - Encrypts the `body` field.
- [!badge variant="info" text="custom_json"] - Encrypts the `json` field. Custom JSON encryption is unique as it wraps the encrypted data in an `encrypted` key.
- [!badge variant="info" text="transfer"] - Encrypts the `memo` field.
- [!badge variant="info" text="transfer_to_savings"] - Encrypts the `memo` field.
- [!badge variant="info" text="transfer_from_savings"] - Encrypts the `memo` field.
- [!badge variant="info" text="recurrent_transfer"] - Encrypts the `memo` field.

!!!secondary Non-encrypted operations
Upon operating in the encrypted transaction builder interface (`startEncrypt` method invoked), operations that are not able to be encrypted will be saved to the transaction as is
!!!

## Encrypting Operations within a Transaction

```typescript
import { createHiveChain } from "@hiveio/wax";

// Assume you have an unlocked wallet instance from BeeKeeper and public key (STM...)
const wallet = /* your unlocked wallet instance */;
const publicKey = "STM..." as TPublicKey;

const hiveChain = await createHiveChain();

// Create a transaction builder
const tx = await hiveChain.getTransactionBuilder();

// Start the encryption chain
tx.startEncrypt(publicKey)
  .push({ // Add encrypted operation
    transfer: {
      from: "alice",
      to: "bob",
      amount: hiveChain.hive(100),
      memo: "This memo will be encrypted"
    }
  })
  .stopEncrypt(); // Stop the encryption chain

// Sign and build the transaction
const signedTx = tx.build(wallet, publicKey);

console.log(signedTx);
```

## Encrypting Operations for Two Accounts within a Transaction

```typescript
import { createHiveChain } from "@hiveio/wax";

// Assume you have an unlocked wallet instance from BeeKeeper and two public keys (STM...)
const wallet = /* your unlocked wallet instance */;
const publicKey1 = "STM..." as TPublicKey;
const publicKey2 = "STM..." as TPublicKey;

const hiveChain = await createHiveChain();

// Create a transaction builder
const tx = await hiveChain.getTransactionBuilder();

// Start the encryption chain with two keys
tx.startEncrypt(publicKey1, publicKey2)
  .push({ // Add encrypted operations
    transfer_to_savings: {
      from: "alice",
      to: "bob",
      amount: hiveChain.hive(100),
      memo: "This memo will be encrypted with two keys"
    }
  })
  .stopEncrypt(); // Stop the encryption chain

// Sign and build the transaction
const signedTx = tx.build(wallet, publicKey1);

console.log(signedTx);
```

These examples demonstrate how to handle encryption and decryption using both direct methods and the transaction builder interface in the Wax library.
