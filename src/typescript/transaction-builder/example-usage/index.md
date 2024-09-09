---
order: -6
icon: flame
label: Example usage
---

# Example Transaction interface usage

Once you know all the `Transaction` interface functionality, let's look at an example of complete usage.

+++ Example usage (HF26 format)

:::code source="../../../static/snippets/src/typescript/transaction-builder/example-usage/example-usage.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/example-usage/example-usage.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fexample-usage%2Fexample-usage.ts&startScript=test-tb-example-usage)" :::

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
        "parent_author": "parent-author",
        "parent_permlink": "parent-permlink",
        "author": "author",
        "permlink": "re-parent-author-1719488687642",
        "title": "",
        "body": "body",
        "json_metadata": "{\"format\":\"markdown+html\",\"app\":\"@hiveio/wax/1.27.6-rc1\",\"tags\":[\"tag\"],\"description\":\"description\"}"
      }
    },
    {
      "type": "comment_options_operation",
      "value": {
        "author": "author",
        "permlink": "re-parent-author-1719488687642",
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
```
===

!!!secondary
Please note that the output for `txSigned` and `txMultiSigned` is not complete due to its complexity. Only the signatures field is presented. You can see the full output in the console by testing it yourself.
!!!

+++ Example usage (Legacy format)

:::code source="../../../static/snippets/src/typescript/transaction-builder/example-usage/example-legacy-usage.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/example-usage/example-legacy-usage.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fexample-usage%2Fexample-legacy-usage.ts&startScript=test-tb-example-legacy-usage)" :::

==- Output

```javascript
// Hive API-legacy form JSON before signing
{
  "ref_block_num": 62661,
  "ref_block_prefix": 599480679,
  "expiration": "2024-07-01T10:43:35",
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

// Hive API-legacy form JSON after signing
{
  "ref_block_num": 63407,
  "ref_block_prefix": 1196655671,
  "expiration": "2024-07-01T11:20:51",
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
  "signatures": [
    "200d601328ce2634744daca1629ae3b83094937592811eb53e75238d1ebddf9fbf4723934be2ab4ad6a0db6151fb7d6bd766289e9cca9e6a1fa258da34c2aa86f2"
  ]
}
```
===

!!!secondary
Also if you want to use some custom tool for signing the transaction instead of our provided methods, you can do it based on the sample above. If you do not want to use `Transaction` interface in legacy form, you can do it just by replacing:

`const digest = tx.legacy_sigDigest;` -> `const digest = tx.sigDigest;`.
!!!

+++ Full Transaction interface example usage

:::code source="../../../static/snippets/src/typescript/transaction-builder/example-usage/full-transaction-builder-usage.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/example-usage/full-transaction-builder-usage.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fexample-usage%2Ffull-transaction-builder-usage.ts&startScript=test-tb-full-example-usage)" :::

==- Output

```javascript
// simpleOperationTx
{
  "ref_block_num": 32100,
  "ref_block_prefix": 27252558,
  "expiration": "2024-07-02T15:56:28",
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
  "signatures": [
    "20fb288dad117d77d18c7880873b165e77954f052ae83a04889744671dfd1f8b97354b3637ad3b16cb5a52a767986748e668ca3ba02fe64f75e3def75a22930755"
  ]
}

// legacyTx
{
  "ref_block_num": 32100,
  "ref_block_prefix": 27252558,
  "expiration": "2024-07-02T15:56:28",
  "operations": [
    [
      "transfer",
      {
        "from": "your-account",
        "to": "friend",
        "amount": "0.100 HIVE",
        "memo": "My transfer operation"
      }
    ]
  ],
  "extensions": [],
  "signatures": [
    "1f5e2496ba8f6d2bcace6f6d244d8d130b053dfc5c17c4474b77a6110d8650451512dc6242cf5149bb2e6ae58b279378af230d71fbe62e2c1685912f4789b68a78"
  ]
}

// encryptionTx
{
  "ref_block_num": 32100,
  "ref_block_prefix": 27252558,
  "expiration": "2024-07-02T15:56:28",
  "operations": [
    {
      "type": "transfer_operation",
      "value": {
        "from": "your-account",
        "to": "friend",
        "amount": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "memo": "#4MWxEsc6QMPu5ifjW1mNpJh6Rx4Li4kaJVxEvNFWysAsggDSLNF6ZEdauVEuompzPXuMuZ4tfTtAadcYXHAXH5ASVCRapttKgx7xEn1S4dydFrM7Uc8jpMmdJ4HDxnhCELxQrxX4iqoFhYaVdYPVq3A8"
      }
    },
    {
      "type": "transfer_operation",
      "value": {
        "from": "your-account",
        "to": "friend",
        "amount": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "memo": "My transfer operation"
      }
    }
  ],
  "signatures": [
    "20768549f9e17688287c6e511a1efa170834dd5ef0662e737de47a874876b83a4812a2f38d1386c1d2ab2ae055282f1ada76646434ad87377a78988c70de36a7ed"
  ]
}

// commentOperationTx
{
  "ref_block_num": 32100,
  "ref_block_prefix": 27252558,
  "expiration": "2024-07-02T15:56:28",
  "operations": [
    {
      "type": "comment_operation",
      "value": {
        "parent_author": "",
        "parent_permlink": "my-category",
        "author": "your-account",
        "permlink": "my-article-permlink",
        "title": "My article title",
        "body": "My article body",
        "json_metadata": "{\"format\":\"markdown\",\"app\":\"@hiveio/wax/1.27.6-rc1\",\"tags\":[\"my-article\"],\"description\":\"This is my article!\",\"image\":[\"article.jpg\"],\"links\":[\"https://example.com\"]}"
      }
    },
    {
      "type": "comment_options_operation",
      "value": {
        "author": "your-account",
        "permlink": "my-article-permlink",
        "max_accepted_payout": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "percent_hbd": 10000,
        "allow_votes": true,
        "allow_curation_rewards": true,
        "extensions": [
          {
            "type": "comment_payout_beneficiaries",
            "value": {
              "beneficiaries": [
                {
                  "account": "friend",
                  "weight": 40
                }
              ]
            }
          }
        ]
      }
    },
    {
      "type": "comment_operation",
      "value": {
        "parent_author": "your-account",
        "parent_permlink": "my-article-permlink",
        "author": "your-account",
        "permlink": "re-your-account-1719935728826",
        "title": "",
        "body": "My reply body",
        "json_metadata": "{\"format\":\"markdown\",\"app\":\"@hiveio/wax/1.27.6-rc1\",\"tags\":[\"my-reply\"],\"description\":\"This is my reply!\",\"image\":[\"reply.jpg\"],\"links\":[\"https://example.com\"]}"
      }
    },
    {
      "type": "comment_options_operation",
      "value": {
        "author": "your-account",
        "permlink": "re-your-account-1719935728826",
        "max_accepted_payout": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "percent_hbd": 10000,
        "allow_votes": true,
        "allow_curation_rewards": true,
        "extensions": [
          {
            "type": "comment_payout_beneficiaries",
            "value": {
              "beneficiaries": [
                {
                  "account": "friend",
                  "weight": 40
                }
              ]
            }
          }
        ]
      }
    }
  ],
  "signatures": [
    "1f1eea6ee1577ae6fedab52ad1cc394b359ea00d0269267e2814a1ea532481329b35ca591a4656414c0fcacd432d40a2ab997f7da29d5686d5cc9207867e0f417d"
  ]
}

// operationFactoriesTx
{
  "ref_block_num": 32101,
  "ref_block_prefix": 2985086707,
  "expiration": "2024-07-02T15:56:29",
  "operations": [
    {
      "type": "recurrent_transfer_operation",
      "value": {
        "from": "your-account",
        "to": "friend",
        "amount": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "memo": "Daily pay",
        "recurrence": 24,
        "executions": 30
      }
    },
    {
      "type": "update_proposal_operation",
      "value": {
        "proposal_id": "1",
        "creator": "your-account",
        "daily_pay": { "amount": "100", "precision": 3, "nai": "@@000000021" },
        "subject": "Proposal Update",
        "permlink": "proposal-update",
        "extensions": [
          {
            "type": "update_proposal_end_date",
            "value": {
              "end_date": "2023-03-14T00:00:00"
            }
          }
        ]
      }
    },
    {
      "type": "witness_set_properties_operation",
      "value": {
        "owner": "your-account",
        "props": [
          [ "account_creation_fee", "307500000000000003535445454d0000" ],
          [ "hbd_interest_rate", "ee02" ],
          [ "key", "03d61d6fa3124160f86e1f870328e4ee1c4956529f3e001a3ce466d192bd4e07ab" ],
          [ "maximum_block_size", "00000100" ],
          [ "url", "1368747470733a2f2f6578616d706c652e636f6d" ]
        ]
      }
    }
  ],
  "signatures": [
    "1fb7cb30e685afdf928d14a8a04a0e8d75511137d72db7e5be0a79d633b54795ee097f2b4cacbfbff1b0f470cbed35146bd35d09ae3987cd6dcf3db0df8bca84e4"
  ]
}

// otherOperationsTx
{
  "ref_block_num": 32101,
  "ref_block_prefix": 2985086707,
  "expiration": "2024-07-02T15:56:29",
  "operations": [
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "follow",
        "json": "[\"follow\",{\"follower\":\"your-account\",\"following\":\"blog-to-follow\",\"what\":[\"blog\"]}]"
      }
    },
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "follow",
        "json": "[\"follow\",{\"follower\":\"your-account\",\"following\":\"blog-to-mute\",\"what\":[\"ignore\"]}]"
      }
    },
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "follow",
        "json": "[\"reblog\",{\"account\":\"your-account\",\"author\":\"to-reblog\",\"permlink\":\"post-permlink\"}]"
      }
    },
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "rc",
        "json": "[\"delegate_rc\",{\"from\":\"your-account\",\"delegatees\":[\"friend\"],\"max_rc\":\"1000\",\"extensions\":[]}]"
      }
    },
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "community",
        "json": "[\"subscribe\",{\"community\":\"communityName\"}]"
      }
    },
    {
      "type": "custom_json_operation",
      "value": {
        "required_posting_auths": [ "your-account" ],
        "id": "community",
        "json": "[\"flagPost\",{\"community\":\"community-name\",\"account\":\"author-account\",\"permlink\":\"post-permlink\",\"notes\":\"violation notes\"}]"
      }
    }
  ],
  "signatures": [
    "1fdce7303d535ca89b99c501113b36076586374d9ddc481519db70c94ea54fd23214b0a8353799008afa35d9f53c5bdd6b943fd132db506b6c5f26854a821dfd7e"
  ]
}
```
===
