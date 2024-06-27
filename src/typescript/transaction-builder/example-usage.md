---
order: -5
icon: flame
label: Example usage
---

# Example Transaction Builder usage

Once you know all the `TransactionBuilder` functionality, let's look at an example of complete usage.

:::code source="../../static/snippets/src/typescript/transaction-builder/example-usage/example-usage.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/example-usage/example-usage.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fexample-usage%2Fexample-usage.ts&startScript=test-tb-example-usage)" :::

==- Output

```javascript
// apiTx
{
  "ref_block_num": 14509,
  "ref_block_prefix": 1156896789,
  "expiration": "2024-06-27T11:45:47",
  "operations": [
    {
      "type": "comment_operation",
      "value": {
        "parent_author": "parent_author",
        "parent_permlink": "parent_permlink",
        "author": "author",
        "permlink": "re-parent_author-1719488687642",
        "title": "",
        "body": "body",
        "json_metadata": "{\"format\":\"markdown+html\",\"app\":\"@hiveio/wax/1.27.6-rc1\",\"tags\":[\"tag\"],\"description\":\"description\"}"
      }
    },
    {
      "type": "comment_options_operation",
      "value": {
        "author": "author",
        "permlink": "re-parent_author-1719488687642",
        "max_accepted_payout": {
          "amount": "1000000000",
          "precision": 3,
          "nai": "@@000000013"
        },
        "percent_hbd": 10000,
        "allow_votes": true,
        "allow_curation_rewards": true,
        "extensions": [
          {
            "type": "comment_payout_beneficiaries",
            "value": {
              "beneficiaries": [
                {
                  "account": "test",
                  "weight": 40
                }
              ]
            }
          }
        ]
      }
    }
  ]
}

// txSigned (only signatures field)
signatures: [
  '1fa3b3153c15633841bedac753ef0770d020b6e67c4325402aa8657556d2feafac4c8ed7a3a7638e0cef5d50e01e91b6a17e8740161f1fda65a9331a02b9cc0ff9'
]

// txMultiSigned (only signatures field)
signatures: [
  '1fa3b3153c15633841bedac753ef0770d020b6e67c4325402aa8657556d2feafac4c8ed7a3a7638e0cef5d50e01e91b6a17e8740161f1fda65a9331a02b9cc0ff9',
  '20562268d6bffe4bebc95dddceccf40479ea8e6a2d079f7d0d2a3627d45b2d1bef7283852299b8a1d64444f89007b90bd92714c3aec8a541906bd0754419d85980'
]

// txBroadcasted
_I {
  max_block_age: -1,
  trx: AI {
    operations: [ [Object], [Object] ],
    extensions: [],
    signatures: [
      '1fa3b3153c15633841bedac753ef0770d020b6e67c4325402aa8657556d2feafac4c8ed7a3a7638e0cef5d50e01e91b6a17e8740161f1fda65a9331a02b9cc0ff9',
      '20562268d6bffe4bebc95dddceccf40479ea8e6a2d079f7d0d2a3627d45b2d1bef7283852299b8a1d64444f89007b90bd92714c3aec8a541906bd0754419d85980'
    ],
    ref_block_num: 14509,
    ref_block_prefix: 1156896789,
    expiration: '2024-06-27T11:45:47'
  }
}
```

===

!!!secondary
Please note that the output for `txSigned` and `txMultiSigned` is not complete due to its complexity. Only the signatures field is presented. You can see the full output in the console by testing it yourself.
!!!