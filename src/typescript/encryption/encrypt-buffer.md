---
order: -1
icon: project-roadmap
---

# Encrypt buffer

The Wax library provides a robust set of tools for handling encryption and decryption within the Hive ecosystem. This includes both methods for direct encryption/decryption as well as using the transaction builder interface to handle encrypted operations.

!!!secondary Public Keys in Hive
One important detail to note is that public keys within the Hive ecosystem start with the prefix `STM`.
!!!

## Using Direct Encryption and Decryption Methods

The `encrypt` and `decrypt` methods allow for straightforward encryption and decryption operations with explicit public keys. Below are examples covering the case with one and two keys:

+++ One key encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-buffer/one-key.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-buffer/one-key.ts](https://stackblitz.com/github/mtyszczak/hive-docs-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-buffer%2Fone-key.ts)" :::

+++ Two keys encryption

:::code source="../../static/snippets/src/typescript/encryption/encrypt-buffer/multiple-keys.ts" language="typescript" title="Test it yourself: [src/typescript/encryption/encrypt-buffer/multiple-keys.ts](https://stackblitz.com/github/mtyszczak/hive-docs-snippets?file=src%2Ftypescript%2Fencryption%2Fencrypt-buffer%2Fmultiple-keys.ts)" :::

+++
