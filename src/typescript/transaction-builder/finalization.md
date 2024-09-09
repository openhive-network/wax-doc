---
order: -3
icon: trophy
label: Finalization
---

# Finalization

When the work with the transaction is ready, you now need to decide what you want to do with it next.

## Conversion to api form

The simple `toApi` method returns the transaction in hive api form:

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/simple-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/simple-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fsimple-build.ts&startScript=test-tb-finalization-simple-build)" :::

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

You can also represent your transaction in the api form, with your signature added to the internal signatures array (it will also apply the transaction expiration time):

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/proto-form-signature-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/proto-form-signature-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fproto-form-signature-build.ts&startScript=test-tb-finalization-proto-form-signature-build)" :::

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

!!!warning Multiple signatures
**Also remember that you can add more than one signature while signing your transaction.**
!!!

If you want to sing your transaction in traditional way and return it in the api form, you can use this sample (it will also apply the transaction expiration time):

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/sign-and-build.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/sign-and-build.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fsign-and-build.ts&startScript=test-tb-finalization-sign-and-build)" :::

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

You can also sign the transaction without converting it to the api form (which will return the signatures):

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/sign.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/sign.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fsign.ts&startScript=test-tb-finalization-sign)" :::

=== Output

```text
1fe8647a82f131671997ce26250bf5a1cb7a18609cbc69b3b2fd7fcaefc848c7fc308abfb0992c1ce9a805715f102416d85c4313a8a00527fa1500ac93898b418a
```

===

!!!danger Beekeeper Information
**If you want to sign the transaction, you have to initialize beekeeper library.** If you want to sign the transaction after creating it, using our `Transaction` interface, you have to initialize our beekeeper library. Remember to import keys into Beekeeper. It ensures that you can use them securely for transactions and other operations without exposing the raw keys.

Imported key and the one you want to use for signing must be the same!
!!!

### Convertions

At the end you can also just convert your transaction into the Hive API-form JSON:

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/convert-to-api.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/convert-to-api.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fconvert-to-api.ts&startScript=test-tb-finalization-convert-to-api)" :::

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

Or you can just convert transction to legacy API form:

:::code source="../../static/snippets/src/typescript/transaction-builder/finalization/convert-to-legacy-api.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/finalization/convert-to-legacy-api.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Ffinalization%2Fconvert-to-legacy-api.ts&startScript=test-tb-finalization-convert-to-legacy-api)" :::

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
