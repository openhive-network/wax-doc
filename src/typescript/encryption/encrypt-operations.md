---
order: -2
icon: fiscal-host
---

# Encrypt operations

Wax provides a simple interface for encrypting operation data within a transaction using the Transaction Builder interface.

## Operations That Can Be Encrypted

Currently, Hive supports encrypting the following operation data:

- [!badge variant="info" text="comment"] - Encrypts the `body` field.
- [!badge variant="info" text="custom_json"] - Encrypts the `json` field. Custom JSON encryption is unique as it wraps the encrypted data in an `encrypted` key.
- [!badge variant="info" text="transfer"] - Encrypts the `memo` field.
- [!badge variant="info" text="transfer_to_savings"] - Encrypts the `memo` field.
- [!badge variant="info" text="transfer_from_savings"] - Encrypts the `memo` field.
- [!badge variant="info" text="recurrent_transfer"] - Encrypts the `memo` field.

!!!secondary Non-encrypted operations
`startEncrypt` only enables encryption for the operation data above, other data is not encrypted.
!!!

## Encrypting Operations within a Transaction

These examples demonstrate how to handle encryption and decryption using both direct methods and the transaction builder interface in the Wax library.

+++ One key encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/one-key.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/one-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fone-key.ts&startScript=test-encryption-encrypt-operations-one-key)" :::

!!!secondary
`publicKey1` used for transaction signing can (and usually does) differ from the public key used for encryption.
!!!

+++ Two keys encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/multiple-keys.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/multiple-keys.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fmultiple-keys.ts&startScript=test-encryption-encrypt-operations-multiple-keys)" :::


+++ Mixed encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/multiple-start-encrypt.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/multiple-start-encrypt.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fmultiple-start-encrypt.ts&startScript=test-encryption-encrypt-operations-multiple-start-encrypt)" :::

!!!secondary
`publicKey1` used for transaction signing can (and usually does) differ from the public key used for encryption.
!!!

+++


