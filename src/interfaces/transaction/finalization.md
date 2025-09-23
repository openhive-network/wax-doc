---
order: -3
icon: trophy
label: Finalization
---

# Finalization

When the work with the transaction is ready, you now need to decide what you want to do with it next.

## Conversion to api form

+++ JavaScript

The simple `toApi` method returns the transaction in the Hive API-JSON form:

:::code source="../../static/snippets/src/typescript/transaction/finalization/simple-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/simple-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fsimple-build.ts&startScript=test-transaction-finalization-simple-build)" :::

==- Output

```javascript
{
  "ref_block_num": 1960,
  "ref_block_prefix": 3915120327,
  "expiration": "2023-11-09T21:51:27",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ]
}
```

===

+++ Python

The simple `toApi` method returns the transaction in the Hive API-JSON form:

:::code source="../../static/snippets/src/python/transaction/finalization/simple_build.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/finalization/simple_build.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/finalization/simple_build.py)" :::

==- Output

```json
{
  "ref_block_num": 48094,
  "ref_block_prefix": 1834167881,
  "expiration": "2025-09-02T12:29:02",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "extensions": [],
  "signatures": []
}
```

===

+++

You can also represent your transaction in the API form, with your signature added to the internal signatures array (it will also apply the transaction expiration time):

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/finalization/proto-form-signature-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/proto-form-signature-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fproto-form-signature-build.ts&startScript=test-transaction-finalization-proto-form-signature-build)" :::

==- Output

```javascript
{
  "ref_block_num": 1960,
  "ref_block_prefix": 3915120327,
  "expiration": "2023-11-09T21:51:27",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "signatures": [
    "signature..."
  ]
}
```

===

+++ Python

:::code source="../../static/snippets/src/python/transaction/finalization/proto_form_signature_build.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/finalization/proto_form_signature_build.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/finalization/proto_form_signature_build.py)" :::

==- Output

```json
{
  "ref_block_num": 48094,
  "ref_block_prefix": 1834167881,
  "expiration": "2025-09-02T12:29:02",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "extensions": [],
  "signatures": ['deadc0de']
}
```

===

+++

!!!warning Multiple signatures
**Also remember that you can add more than one signature while signing your transaction.**
!!!

If you want to sign your transaction in traditional way and return it in the API form, you can use this sample (it will also apply the transaction expiration time):

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/finalization/sign-and-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/sign-and-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fsign-and-build.ts&startScript=test-transaction-finalization-sign-and-build)" :::

==- Output

```javascript
{
  "ref_block_num": 1960,
  "ref_block_prefix": 3915120327,
  "expiration": "2023-11-09T21:51:27",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "signatures": [
    "1fe8647a82f131671997ce26250bf5a1cb7a18609cbc69b3b2fd7fcaefc848c7fc308abfb0992c1ce9a805715f102416d85c4313a8a00527fa1500ac93898b418a"
  ]
}
```

===

+++ Python

:::code source="../../static/snippets/src/python/transaction/finalization/sign_and_build.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/finalization/sign_and_build.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/finalization/sign_and_build.py)" :::

==- Output

```json
{
  "ref_block_num": 50325,
  "ref_block_prefix": 551408451,
  "expiration": "2025-09-02T14:20:48",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "extensions": [],
  "signatures": [
    "1fb3c5117c8a01459ce106f949dae1cf5ad9609b1eaa3fc49be5d418acabd0ad69549306d5df8667cc8487c2e5c20ad21380d42c1c5abe6918e94bbe5f5f4fb66e"
  ]
}
```

===

+++

You can also sign the transaction without converting it to the API form (which will return the signatures):

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/finalization/sign.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/sign.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fsign.ts&startScript=test-transaction-finalization-sign)" :::

=== Output

```text
1fe8647a82f131671997ce26250bf5a1cb7a18609cbc69b3b2fd7fcaefc848c7fc308abfb0992c1ce9a805715f102416d85c4313a8a00527fa1500ac93898b418a
```

===

+++ Python

:::code source="../../static/snippets/src/python/transaction/finalization/sign.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/finalization/sign.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/finalization/sign.py)" :::

==- Output

```text
1fde4f09e326c69f4321e517e512770ef05986b1f33ad6fadcea75f54cf49beeb80fab11e45416adae97ed78a207b7d3950f24c78fb5ce1d0dfa1d5370f0f383ea
```

===

+++

!!!danger Beekeeper Information
If you want to sign the transaction after creating it, using our `ITransaction` interface, you should use one of the available [signers](../signers). Remember to import keys into Beekeeper. It ensures that you can use them securely for transactions and other operations without exposing the raw keys.

Imported key and the one you want to use for signing must be the same!
!!!

### Conversions

At the end you can also just convert your transaction into the Hive API-form JSON:

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/finalization/convert-to-api.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/convert-to-api.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fconvert-to-api.ts&startScript=test-transaction-finalization-convert-to-api)" :::

==- Output

```json
{
  "ref_block_num": 1960,
  "ref_block_prefix": 3915120327,
  "expiration": "2023-11-09T21:51:27",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ]
}
```

===

+++ Python

:::code source="../../static/snippets/src/python/transaction/finalization/convert_to_api.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/finalization/convert_to_api.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/finalization/convert_to_api.py)" :::

==- Output

```json
{
  "ref_block_num": 50730,
  "ref_block_prefix": 1097976323,
  "expiration": "2025-09-02T14:41:07",
  "operations": [
    {
      "type": "vote_operation",
      "value": {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    }
  ],
  "extensions": [],
  "signatures": []
}
```

===

+++

Or you can just convert transction to legacy API form:

+++ JavaScript

:::code source="../../static/snippets/src/typescript/transaction/finalization/convert-to-legacy-api.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/finalization/convert-to-legacy-api.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Ffinalization%2Fconvert-to-legacy-api.ts&startScript=test-transaction-finalization-convert-to-legacy-api)" :::

==- Output

```json
{
  "ref_block_num": 1960,
  "ref_block_prefix": 3915120327,
  "expiration": "2023-11-09T21:51:27",
  "operations": [
    [
      "vote",
      {
        "voter": "voter",
        "author": "test-author",
        "permlink": "test-permlink",
        "weight": 2200
      }
    ]
  ],
  "extensions": [],
  "signatures": []
}
```

===

+++ Python

```text
The legacy transaction format is deprecated — wax-python no longer supports this conversion.
```

+++
