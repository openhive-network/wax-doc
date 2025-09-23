---
order: -1
icon: passkey-fill
---

# Generating private keys

Hive layer 1 keys can be generated via two methods:

1. Derivation of a set of private keys from a password (sometimes referred to as a "Master Password"). This is typically used to initially create active, owner, posting, and memo keys for a Hive account.
2. Randomly generate a new private key (generally should only be used in one-time-use scenarios).

## Generate a private key for an account role from a password

!!!danger
The master password should always be a truly random and secure value
!!!

+++ JavaScript

:::code source="../../static/snippets/src/typescript/key-generation/generate-key/generate-private-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/generate-key/generate-private-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fkey-generation%2Fgenerate-key%2Fgenerate-private-key.ts&startScript=test-key-generation-generate-key-generate-private-key)" :::

+++ Python
:::code source="../../static/snippets/src/python/generate_keys.py" language="python" range=3-4,6-7,14-23 title="Test it yourself on github codespace: [src/python/generate_keys.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/generate_keys.py)" :::

==- Output

```log
Results from Password-derived key generation:
Private key: 5JTxtE9jdDu43PUCr3ip2KWnWFoofD7dfkPWA9gREN1jn6YwZat
Public key: STM8b2ESwQaEBJq1AtnXqLSD5S1jSTNmijzoZNqQtok3FBoQFtQTr
```

===
+++

## Suggest Brain Key

A brain key is a long passphrase that provides enough entropy to generate cryptographic keys. The `suggestBrainKey` function returns a brain key along with the corresponding private and public keys.

Using a brain key, you can regenerate the same key pairs whenever needed, provided the exact same mnemonic phrase is used. This is especially useful in scenarios requiring backup and recovery of cryptographic keys, ensuring they are never permanently lost.

+++ JavaScript

:::code source="../../static/snippets/src/typescript/key-generation/generate-key/suggest-brain-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/generate-key/suggest-brain-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fkey-generation%2Fgenerate-key%2Fsuggest-brain-key.ts&startScript=test-key-generation-suggest-brain-key)" :::

+++ Python

:::code source="../../static/snippets/src/python/generate_keys.py" language="python" range=3-4,6-7,31-35 title="Test it yourself on github codespace: [src/python/generate_keys.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/generate_keys.py)" :::

==- Output

```log
Seed phrase: MEMO FAUST DOB CHARGE WAXILY BURSATE POPWEED TOOTHY PEDICEL NICOTIC GUTTIDE SAVANT BUNT MOMME HORNIFY UNOIL
Private key: 5KhKdhiVPpJrMqamx4VukXtBPh7VDWfZvJsv2xdcHBHDRFanVKN
Public key: STM5Br7eDvpXavuxfajqDfhRu6cmVRzRq1z26ch4Dx9b4hoZxKgJt
```

===

+++

!!!danger Security Reminder
**Always save the generated private keys and password securely.** These keys provide access to your Hive account and assets. You can import them into the Beekeeper or any other [supported Hive wallet](../signers) to ensure that you can use them securely for transactions and other operations without exposing the raw keys.
!!!
