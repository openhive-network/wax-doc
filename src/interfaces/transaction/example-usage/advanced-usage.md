---
order: -1
icon: webhook
label: Advanced usage
---

# Advanced usage

If you want to use the advanced features of the `ITransaction` interface you can initalize it using dedicated methods:

## Initialization with explicit TaPoS and expiration time

Creating transaction with TaPoS can be useful for cases when you would like to perform batch operations without any access to remote Hive API calls.

Due to long TaPoS lifespan (near to 64000 blocks, so it really targets to the c.a. 3 hours), you can easily receive TaPoS data (reference block-id) once from blockchain and next reuse it in your code generating massive transactions, to finally sign and broadcast them:

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/example-usage/advanced-usage/explicit-data-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/example-usage/advanced-usage/explicit-data-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fexample-usage%2Fadvanced-usage%2Fexplicit-data-initialization.ts&startScript=test-transaction-full-advanced-usage-explicit-data)" :::

+++ Python

TBA

+++

## Initialization from hive API-JSON form

This can be useful for analyzing transactions retrieved from the API or restored previously from the API form.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/example-usage/advanced-usage/api-form-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/example-usage/advanced-usage/api-form-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fexample-usage%2Fadvanced-usage%2Fapi-form-initialization.ts&startScript=test-transaction-full-advanced-usage-api-form)" :::

+++ Python

TBA

+++

## Initialize from protobuf transaction

This can be useful for analyzing transactions restored previously from the protobuf form.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/example-usage/advanced-usage/protobuf-transaction-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/example-usage/advanced-usage/protobuf-transaction-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fexample-usage%2Fadvanced-usage%2Fprotobuf-transaction-initialization.ts&startScript=test-transaction-full-advanced-usage-protobuf)" :::

+++ Python

TBA

+++
