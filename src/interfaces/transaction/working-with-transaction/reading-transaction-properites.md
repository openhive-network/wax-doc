---
order: -3
icon: book
label: Reading properties
---

# Reading transaction properties

The `ITransaction` interface also allows you to read your transaction properties like sig digest, id, etc.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/reading-transaction-properties/reading-properties.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/reading-transaction-properties/reading-properties.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Freading-transaction-properties%2Freading-properties.ts&startScript=test-transaction-working-with-transaction-reading-properties)" :::

=== Output

```text
id: 8b61be0b5b857f2a9be8a65ac5d8461d2b091e30
sigDigest: d552081de1d55636a97633a3dc75a85854e83a574bcbbcffd69dcd7fcb4dcc58
expiration: 2024-09-06T12:33:58
ref_block_num: 1960
```

===

+++ Python

:::code source="../../../static/snippets/src/python/transaction/working_with_transaction/reading_transaction_properties/reading_properties.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/working_with_transaction/reading_transaction_properties/reading_properties.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/working_with_transaction/reading_transaction_properties/reading_properties.py)" :::

=== Output

```text
id: f0d64ae54e9ae84dbdabb3d6987484db5868aedc
sig_digest: 14e066439ceb222e911e052583431c47a7d9afaa53732c16990f3d4b0c145cd5
expiration: 2025-09-05T13:11:08
ref_block_num: 4170
```

===

+++
