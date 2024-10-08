---
order: -2
icon: file-moved
---

# Using RecurrentTransfer

The `RecurrentTransferOperation` allows for initiating, modifying, and removing recurrent transfers on the Hive blockchain.

## Creating a new Recurrent Transfer

:::code source="../../../static/snippets/src/typescript/transaction-builder/operation-factories/recurrent-transfer/creating-recurrent-transfer.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/operation-factories/recurrent-transfer/creating-recurrent-transfer.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Foperation-factories%2Frecurrent-transfer%2Fcreating-recurrent-transfer.ts&startScript=test-tb-operation-factories-creating-recurrent-transfer)" :::

## Generate Removal Using RecurrentTransferOperation

Generate removal removes recurrent transfer:

:::code source="../../../static/snippets/src/typescript/transaction-builder/operation-factories/recurrent-transfer/generate-removal.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/operation-factories/recurrent-transfer/generate-removal.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Foperation-factories%2Frecurrent-transfer%2Fgenerate-removal.ts&startScript=test-tb-operation-factories-generate-removal)" :::

## Add Pair Id

In this example we add pair id to recurrent transfer, using `RecurrentTransferOperation` (simply specify the `pairId` field in the configuration):

:::code source="../../../static/snippets/src/typescript/transaction-builder/operation-factories/recurrent-transfer/add-pair-id.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/operation-factories/recurrent-transfer/add-pair-id.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Foperation-factories%2Frecurrent-transfer%2Fadd-pair-id.ts&startScript=test-tb-operation-factories-add-pair-id)" :::
