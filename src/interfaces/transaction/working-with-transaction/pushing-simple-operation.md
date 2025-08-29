---
order: -1
icon: milestone
label: Simple operation
---

# Pushing simple operation

If your case is to perform simple actions on your transaction or create a new transaction, you can use initialization with the wax base interface.

!!! secondary
However it is recommended to use chain initialization due to automatic TaPos data fetching (and so we do in the example code below).
!!!

Below is an example of fully building a simple transaction using the basic `ITransaction` interface.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/pushing-simple-operation/simple-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/pushing-simple-operation/simple-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Fpushing-simple-operation%2Fsimple-operation.ts&startScript=test-transaction-working-with-transaction-simple-operation)" :::

=== Output

```javascript
[
  {
    vote_operation: {
      voter: 'voter',
      author: 'test-author',
      permlink: 'test-permlink',
      weight: 2200
    }
  }
]
```

===

+++ Python

TBA

+++
