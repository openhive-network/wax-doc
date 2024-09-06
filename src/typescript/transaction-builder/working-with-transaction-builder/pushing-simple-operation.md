---
order: -2
icon: milestone
label: Simple operation
---

# Pushing simple operation

If your case is to perform simple actions on your transaction or create a new transaction, you can use initialization with the wax base interface.

Below is an example of fully building a simple transaction using the basic `Transaction` interface.

:::code source="../../../static/snippets/src/typescript/transaction-builder/working-with-tb/simple-operation/simple-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/working-with-tb/simple-operation/simple-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fworking-with-tb%2Fsimple-operation%2Fsimple-operation.ts&startScript=test-tb-working-with-tb-simple-operation)" :::

=== Output

```javascript
[
  {
    vote: {
      voter: 'voter',
      author: 'test-author',
      permlink: 'test-permlink',
      weight: 2200
    }
  }
]
```

===
