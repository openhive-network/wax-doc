---
order: -1
icon: cpu
label: Initialization
---

# Creating a Transaction

The code below shows how to create a new transaction, having TaPoS (reference block) data automatically fetched from the remote Hive API endpoint. This implicitly creates an instance of [Online transaction](./working-with-transaction/online-transaction):

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/initialization/from-remote-initialization.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/initialization/from-remote-initialization.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Finitialization%2Ffrom-remote-initialization.ts&startScript=test-transaction-initialization-from-remote-initialization)" :::

+++ Python

:::code source="../../static/snippets/src/python/transaction/initialization/from_remote_initialization.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/initialization/from_remote_initialization.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/initialization/from_remote_initialization.py)" :::

+++
