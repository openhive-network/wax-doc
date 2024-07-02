---
order: -3
icon: graph
label: Complex operation
---

# Adding complex operations

If you want to work with `TransactionBuilder` in more complex way, it is recommendet to initialize it from hive chain interface. It allows you to avoid complexity of your work.

Below is an example of fully building more complex transaction using the `TransactionBuilder` interface and our `useBuilder` functionality.

:::code source="../../../static/snippets/src/typescript/transaction-builder/working-with-tb/complex-operation/complex-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/working-with-tb/complex-operation/complex-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fworking-with-tb%2Fcomplex-operation%2Fcomplex-operation.ts&startScript=test-tb-working-with-tb-complex-operation)" :::

=== Output

```javascript
{
  witness_set_properties: {
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

The `useBuilder` method allows for simple construction of an operation. It takes the following parameters:
- The constructor of the builder class you want to use,
- An arrow function, inside which you can make use of all the methods available within the given builder,
- Other arguments specific to the given builder.

The `useBuilder` method returns an instance of `TransactionBuilder`, on which you can later perform operations related to the transaction.

More complex information about `useBuilder` are presented in subsequent chapters.