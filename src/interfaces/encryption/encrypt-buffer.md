---
order: -1
icon: project-roadmap
---

# Encrypt buffer

The Wax library provides a robust set of tools for handling encryption and decryption within the Hive ecosystem. This includes both methods for direct encryption/decryption as well as using the `ITransaction` interface to handle encrypted operations.

!!!secondary Public Keys in Hive
One important detail to note is that public keys within the Hive ecosystem start with the prefix `STM`.
!!!

## Using Direct Encryption and Decryption Methods

The signer's `encryptData` and `decryptData` methods allow for straightforward encryption and decryption operations with explicit public keys. You provide the content as a string to be encrypted/decrypted, and the public key(s) used for encryption/decryption. Below are examples covering the case with one and two keys (sender key and receiver key):

### One key encryption

+++ JavaScript

:::code source="../../static/snippets/src/typescript/encryption/encrypt-buffer/one-key.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-buffer/one-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-buffer%2Fone-key.ts&startScript=test-encryption-encrypt-buffer-one-key)" :::

+++ Python

**Not implemented yet** — planned for a future release.

+++

### Two keys encryption

+++ JavaScript

:::code source="../../static/snippets/src/typescript/encryption/encrypt-buffer/multiple-keys.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-buffer/multiple-keys.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-buffer%2Fmultiple-keys.ts&startScript=test-encryption-encrypt-buffer-multiple-keys)" :::

+++ Python

**Not implemented yet** — planned for a future release.

+++

!!!secondary
A second public key is passed to the encryption method in this example for later use during decryption - matching public key to the private key in the wallet.
!!!

!!!danger Using private keys
The public key you are providing to the signer's `encryptData`/`decryptData` methods should correspond to private keys that are available in your signer instance. If the requested private key for the given public key is not found in the signer, an exception will be thrown.
!!!
