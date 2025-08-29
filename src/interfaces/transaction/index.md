---
order: -5
icon: database
expanded: false
label: Creating transactions
---

# Transactions

A `ITransaction` is an interface for building, signing, and validating transactions.

The `ITransaction` in the Hive Ecosystem, provided by the `@hiveio/wax` library, is a tool for creating and managing transactions on the Hive blockchain. It offers functionalities for building, signing, validating, and converting transactions.

## Beekeeper initialization

Beekeeper is a library that provides security in storing your keys. With it, you can easily import keys stored in your wallet and use them to sign your transactions. This is an incredibly useful tool in the context of working with the `ITransaction` interface, which you will have the opportunity to see in the following chapters.

+++ JavaScript

In our test environment, we have used Beekeeper in [`runner.js`](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=scripts%2Frunner.js). Thanks to this functionality, to execute code examples, you can utilize specific functionalities of Beekeeper (wallet, privateKey, etc.) by simply destructuring the object available in globalThis:

```javascript
// Here are presented all the available variables that can be used in the examples.
const { wallet, password, publicKey1, publicKey2 } = globalThis.snippetsBeekeeperData
```

+++ Python

TBA

+++
