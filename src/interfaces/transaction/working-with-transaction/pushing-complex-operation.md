---
order: -2
icon: graph
label: Complex operation
---

# Adding complex operations

Complex usage of `ITransaction` interface allows to:

- manually initialize transaction object with some blockchain properties (like TaPoS)
- use provided operation factory classes which encapsulate blockchain complexity (this part operates on any transaction object - regardless of way how you obtained it)

Below is a complete example of a blockchain operation, requiring explicit serialization of input data to properly build final operation. All such steps require complex knowledge of blockchain internals and have been adopted to "regular programming steps".

+++ JavaScript

Here we utilize `WitnessSetPropertiesOperation` class to build a complex operation using simple interface:

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/pushing-complex-operation/complex-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/pushing-complex-operation/complex-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Fpushing-complex-operation%2Fcomplex-operation.ts&startScript=test-transaction-working-with-transaction-complex-operation)" :::

=== Output

```javascript
{
  witness_set_properties_operation: {
    owner: 'owner',
    props: {
      key: '02472d6eb6d691b6de8b103b51ebdf4e128a523946d8cd03d6ded91b1497ee2e83',
      url: '1368747470733a2f2f6578616d706c652e636f6d'
    },
    extensions: []
  }
}
```

===

+++ Python

:::code source="../../../static/snippets/src/python/transaction/working_with_transaction/pushing_complex_operation/complex_operation.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/working_with_transaction/pushing_complex_operation/complex_operation.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/working_with_transaction/pushing_complex_operation/complex_operation.py)" :::

==- Output

```python
witness_set_properties_operation {
  owner: "alice"
  props {
    key: "url"
    value: "1368747470733a2f2f6578616d706c652e636f6d"
  }
  props {
    key: "key"
    value: "021df13f04fc422c703043db939c2f98a600fafd0f719a0ff351b8e36c5cad2eff"
  }
}
```

===

+++

As usually, the "push operation" method allows you to push any operation (regadless to complexity related to given blockchain scenario, being encapsulated by used operation class).
At the end, the "push operation" method returns an instance of `ITransaction` interface, on which you can later perform operations related  to the transaction. It nicely reuses well known scheme: [Call-chain](https://refactoring.guru/design-patterns/chain-of-responsibility/)

More complex information about `pushOperation` are presented in subsequent chapters.
