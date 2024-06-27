---
order: -1
icon: rocket
label: Initialization
---

# Initializing a Transaction Builder

Once you want to initiliaze `TransactionBuilder` with explicit reference Block data (to satisfy TAPOS) and transaction expiration time:

:::code source="../../static/snippets/src/typescript/transaction-builder/initialization/explicit-data-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/initialization/explicit-data-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Finitialization%2Fexplicit-data-initialization.ts&startScript=test-tb-initialization-explicit-data-initialization)" :::

Once you have your protobuf transaction ready, you can provide it while constructing:

:::code source="../../static/snippets/src/typescript/transaction-builder/initialization/protobuf-transaction-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/initialization/protobuf-transaction-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Finitialization%2Fprotobuf-transaction-initialization.ts&startScript=test-tb-initialization-protobuf-transaction-initialization)" :::

Once you have your transaction in Hive API-form and you want to convert it to our `TransactionBuilder`:

:::code source="../../static/snippets/src/typescript/transaction-builder/initialization/api-form-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/initialization/api-form-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Finitialization%2Fapi-form-initialization.ts&startScript=test-tb-initialization-api-form-initialization)" :::

Once you want to have "ready to use" `TransactionBuilder` with reference block data from the remote:

:::code source="../../static/snippets/src/typescript/transaction-builder/initialization/from-remote-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/initialization/from-remote-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Finitialization%2Ffrom-remote-initialization.ts&startScript=test-tb-initialization-from-remote-initialization)" :::
