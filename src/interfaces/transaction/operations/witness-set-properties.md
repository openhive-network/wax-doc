---
order: -4
icon: people
---

# Setting Witness Properties

The Witness Set Properties Operation allows witnesses to update their properties on the Hive blockchain.

## Setting Default Witness Properties

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/witness-set-properties/default-witness-properties.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/witness-set-properties/default-witness-properties.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Fwitness-set-properties%2Fdefault-witness-properties.ts&startScript=test-transaction-operations-default-witness-properties)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/witness_set_properties/default_witness_set_properties.py" language="python" title="Test it yourself on github codespace: [src/static/snippets/src/python/transaction/operations/witness_set_properties/default_witness_set_properties.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=kudmich/python-snippets&file=workspaces/wax-doc-snippets/src/python/transaction/operations/witness_set_properties/default_witness_set_properties.py)" :::

==- Output

```python
{
  "ref_block_num": 50355,
  "ref_block_prefix": 2819025043,
  "expiration": "2025-09-09T10:22:31",
  "operations": [
    {
      "witness_set_properties_operation": {
        "owner": "witness-account",
        "props": {
          "key": "020331b0a4dfd5d160aff217aaa98b765f56bc9254cef83f198e1f17ea892a4df3"
        }
      }
    }
  ]
}
```

===

+++

## Setting Explicit Witness Properties

As with all operation classes, you can set all the optional fields on a single class instance.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/witness-set-properties/set-explicit.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/witness-set-properties/set-explicit.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Fwitness-set-properties%2Fset-explicit.ts&startScript=test-transaction-operations-set-explicit)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/witness_set_properties/set_explicit.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/witness_set_properties/set_explicit.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=kudmich/python-snippets&file=workspaces/wax-doc-snippets/src/python/transaction/operations/witness_set_properties/set_explicit.py)" :::

==- Output

```python
{
  "ref_block_num": 50303,
  "ref_block_prefix": 1313275612,
  "expiration": "2025-09-09T10:19:54",
  "operations": [
    {
      "witness_set_properties_operation": {
        "owner": "witness-account",
        "props": {
          "key": "020331b0a4dfd5d160aff217aaa98b765f56bc9254cef83f198e1f17ea892a4df3",
          "hbd_interest_rate": "ee02",
          "maximum_block_size": "00000100",
          "account_creation_fee": "e8030000000000002320bcbe",
          "url": "1b68747470733a2f2f7769746e6573732e6578616d706c652e636f6d"
        }
      }
    }
  ]
}
```

===

+++
