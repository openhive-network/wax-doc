---
order: -1
icon: passkey-fill
---

# Generating private keys

Hive layer 1 keys can be generated via two methods:

1. Derivation of a set of private keys from a password (sometimes referred to as a "Master Password"). This is typically used to initially create active, owner, posting, and memo keys for a Hive account.
2. Randomly generate a new private key (generally should only be used in one-time-use scenarios).

## Generate a private key for an account role from a password

+++ JavaScript

:::code source="../../static/snippets/src/typescript/key-generation/generate-key/generate-private-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/generate-key/generate-private-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fkey-generation%2Fgenerate-key%2Fgenerate-private-key.ts&startScript=test-key-generation-generate-key-generate-private-key)" :::

+++ Python

TBA

+++

## Suggest Brain Key

A brain key is a long passphrase that provides enough entropy to generate cryptographic keys. The `suggestBrainKey` function returns a brain key along with the corresponding private and public keys.

Using a brain key, you can regenerate the same key pairs whenever needed, provided the exact same mnemonic phrase is used. This is especially useful in scenarios requiring backup and recovery of cryptographic keys, ensuring they are never permanently lost.

## Generate a random private key

+++ JavaScript

:::code source="../../static/snippets/src/typescript/key-generation/generate-key/suggest-brain-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/generate-key/suggest-brain-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fkey-generation%2Fgenerate-key%2Fsuggest-brain-key.ts&startScript=test-key-generation-suggest-brain-key)" :::

+++ Python

TBA

+++

!!!danger Security Reminder
**Always save the generated private keys and password securely.** These keys provide access to your Hive account and assets. You can import them into the Beekeeper or any other [supported Hive wallet](../../signers) to ensure that you can use them securely for transactions and other operations without exposing the raw keys.
!!!
