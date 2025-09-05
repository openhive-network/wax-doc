---
order: -5
icon: log
expanded: false
label: Creating transactions
---

# Transactions

A `ITransaction` is an interface for building, signing, and validating transactions.

The `ITransaction` in the Hive Ecosystem, provided by the Wax library, is a tool for creating and managing transactions on the Hive blockchain. It offers functionalities for building, signing, validating, and converting transactions.

## Transaction signing

Signing a transaction is a crucial step in ensuring its authenticity and integrity. The `ITransaction` interface provides methods for signing transactions using dedicated [signers](../signers/). This process involves creating a digital signature that verifies the transaction's origin and prevents tampering.

In our examples, we used a Beekeeper package that provides security in storing your keys. With it, you can easily import keys stored in your wallet and use them to sign transaction digests (signing-ready hashes). Beekeeper is available in multiple languages:

- TypeScript: [`@hiveio/beekeeper`](https://www.npmjs.com/package/@hiveio/beekeeper)
- Python: TBA

+++ JavaScript

In our test environment, we have used Beekeeper in [`runner.js`](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=scripts%2Frunner.js). Thanks to this functionality, to execute code examples, you can utilize specific functionalities of Beekeeper (wallet, privateKey, etc.) by simply destructuring the object available in globalThis:

```javascript
/*
Here are presented all the available variables that can be used in the examples:

  `signer1`    - Beekeeper signer holding wallet with imported private key for publicKey1
  `signer2`    - Beekeeper signer holding wallet with imported private key for publicKey2
  `wallet`     - Raw Beekeeper wallet instance holding both keys for example usage of manually
                 signing using transaction digest (in both: legacy and HF26 ways)
  `publicKey1` - Public key corresponding to the first imported private key
  `publicKey2` - Public key corresponding to the second imported private key
*/
const { signer1, signer2, wallet, publicKey1, publicKey2 } = globalThis.snippetsBeekeeperData;
```

!!!secondary
You can also use any other [signer](../signers/) to sign transactions instead of `signer1` or `signer2`.

We used Beekeeper in our examples for its simplicitly and security in handling private keys in multiple environments (Node.js, browser, etc.).
!!!

+++ Python

:::code source="../../static/snippets/src/python/beekeeper_initialize.py" language="python" title="Test it yourself on github codespace: [src/python/beekeeper_initialize.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=kudmich/python-snippets&file=workspaces/wax-doc-snippets/src/static/snippets/python/beekeeper_initialize.py)" :::

+++
