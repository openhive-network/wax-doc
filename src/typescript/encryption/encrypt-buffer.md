---
order: -1
icon: project-roadmap
---

# Encrypt buffer

The Wax library provides a robust set of tools for handling encryption and decryption within the Hive ecosystem. This includes both methods for direct encryption/decryption as well as using the transaction builder interface to handle encrypted transactions.

## Public Keys in Hive

One important detail to note is that public keys within the Hive ecosystem start with the prefix `STM`.

## Using Direct Encryption and Decryption Methods

The `encrypt` and `decrypt` methods allow for straightforward encryption and decryption operations with explicit public keys. Below are examples covering the case with one and two keys:

```typescript
import { createHiveChain } from "@hiveio/wax";

// Assume you have an unlocked wallet instance from BeeKeeper and public key (STM...)
const wallet = /* your unlocked wallet instance */;
const publicKey = "STM..." as TPublicKey;

const hiveChain = await createHiveChain();
const content = "This is a secret message.";

// Encrypt the content
const encryptedContent = hiveChain.encrypt(wallet, content, publicKey);

// Decrypt the content
const decryptedContent = hiveChain.decrypt(wallet, encryptedContent);

console.log(decryptedContent); // This is a secret message.
```

## Encrypting and Decrypting with Two Keys

```typescript
import { createHiveChain } from "@hiveio/wax";

// Assume you have an unlocked wallet instance from BeeKeeper and two public keys (STM...)
const wallet = /* your unlocked wallet instance */;
const publicKey1 = "STM..." as TPublicKey;
const publicKey2 = "STM..." as TPublicKey;

const hiveChain = await createHiveChain();
const content = "This is a secret message.";

// Encrypt the content using two keys
const encryptedContent = hiveChain.encrypt(wallet, content, publicKey1, publicKey2);

// Decrypt the content
const decryptedContent = hiveChain.decrypt(wallet, encryptedContent);

console.log(decryptedContent); // This is a secret message.
```
