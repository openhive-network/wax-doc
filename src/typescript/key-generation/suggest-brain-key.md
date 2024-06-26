---
order: -2
icon: key-asterisk
---

# Suggest brain key

A brain key is a long passphrase that provides enough entropy to generate cryptographic keys. The `suggestBrainKey` function returns a brain key along with the corresponding private and public keys.

Using a brain key, you can regenerate the same key pairs whenever needed, provided the exact same mnemonic phrase is used. This is especially useful in scenarios requiring backup and recovery of cryptographic keys, ensuring they are never permanently lost.

## Code Snippet to Suggest a Brain Key

:::code source="../../static/snippets/src/typescript/key-generation/suggest-brain-key/suggest-brain-key.ts" language="typescript" title="Test it yourself: [src/typescript/key-generation/suggest-brain-key/suggest-brain-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fkey-generation%2Fsuggest-brain-key%2Fsuggest-brain-key.ts&startScript=test-key-generation-suggest-brain-key)" :::

!!!danger Security Reminder
Generated keys or brain keys should always be stored securely. **Do not share your private keys or brain key with anyone.** These keys are crucial for accessing your Hive account, and sharing them could result in unauthorized access to your assets. Importing them into secure storage solutions like Beekeeper allows safe usage without exposing them directly.
!!!
