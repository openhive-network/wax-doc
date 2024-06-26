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

+++ One key encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/one-key.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/one-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fone-key.ts)" :::

!!!secondary
`publicKey1` used here for the transaction signing may differ from the public key used for operations encryption
!!!

+++ Two keys encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/multiple-keys.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/multiple-keys.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fmultiple-keys.ts)" :::

!!!secondary
`publicKey1` used here for the transaction signing may differ from the public key used for operations encryption
!!!

+++ Mixed encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-operations/multiple-start-encrypt.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-operations/multiple-start-encrypt.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-operations%2Fmultiple-start-encrypt.ts)" :::

!!!secondary
`publicKey1` used here for the transaction signing may differ from the public key used for operations encryption
!!!

+++

These examples demonstrate how to handle encryption and decryption using both direct methods and the transaction builder interface in the Wax library.
