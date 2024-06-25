---
order: -1
icon: passkey-fill
---

# Generate Private Key

In the context of the Hive ecosystem and specifically using the `@hiveio/wax` library, key generation can be achieved through two primary methods:

1. Derivation of a private key from a password (commonly referred to as a "Master Password" or "Brain Key").
2. Generation of a new private key (suggest brain key).

You can derive a private key from a password. This method is useful if you have a strong password and want to generate a private key for specific roles (active, owner, posting, memo) in your Hive account.

## Code Snippet to Generate a New Private Key or a Private Key from Password

:::code source="../../static/snippets/src/typescript/key-generation/generate-key/generate-private-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/generate-key/generate-private-key.ts](https://stackblitz.com/github/mtyszczak/hive-docs-snippets?file=src%2Ftypescript%2Fkey-generation%2Fgenerate-key%2Fgenerate-private-key.ts)" :::

!!!danger Security Reminder
**Always save the generated private keys and brain keys securely.** These keys provide access to your Hive account and assets. Importing them into Beekeeper ensures that you can use them securely for transactions and other operations without exposing the raw keys.
!!!
