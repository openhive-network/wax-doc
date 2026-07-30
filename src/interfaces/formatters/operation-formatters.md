---
order: -3
icon: tasklist
---

# Operation Formatters

## Formatting RC delegation operations

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/operation-formatters/rc-delegate.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/operation-formatters/rc-delegate.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Foperation-formatters%2Frc-delegate.ts&startScript=test-formatters-operation-formatters-rc-delegate)" :::

==- Output

```javascript
[{
  custom_json_operation: {
    delegatees: [ "gtg", "null" ],
    from: "initminer",
    rc: {
      amount: "4127361273",
      nai: "@@000000037",
      precision: 6,
    }
  }
}, {
  custom_json_operation: {
    delegatees: [ "null" ],
    from: "initminer",
    rc: {
      amount: "0",
      nai: "@@000000037",
      precision: 6,
    }
  }
}]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

:::code source="../../static/snippets/src/rust/formatters/operation_formatters/rc_delegate.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/operation_formatters/rc_delegate.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/operation_formatters/rc_delegate.rs)" :::

==- Output

```json
[
  {
    "custom_json_operation": {
      "delegatees": ["gtg", "null"],
      "from": "initminer",
      "rc": {
        "amount": "4127361273",
        "nai": "@@000000037",
        "precision": 6
      }
    }
  },
  {
    "custom_json_operation": {
      "delegatees": ["null"],
      "from": "initminer",
      "rc": {
        "amount": "0",
        "nai": "@@000000037",
        "precision": 6
      }
    }
  }
]
```

===

+++

## Formatting community operations

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/operation-formatters/community.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/operation-formatters/community.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Foperation-formatters%2Fcommunity.ts&startScript=test-formatters-operation-formatters-community)" :::

==- Output

```javascript
[{
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.FLAG_POST,
      account: "gtg",
      permlink: "first-post",
      notes: "note",
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.MUTE_POST,
      account: "gtg",
      permlink: "first-post",
      notes: "note",
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.PIN_POST,
      account: "gtg",
      permlink: "first-post",
      notes: undefined,
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.SUBSCRIBE,
      account: undefined,
      permlink: undefined,
      notes: undefined,
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.UNMUTE_POST,
      account: "gtg",
      permlink: "first-post",
      notes: "note",
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.UNPIN_POST,
      account: "gtg",
      permlink: "first-post",
      notes: undefined,
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.UNSUBSCRIBE,
      account: undefined,
      permlink: undefined,
      notes: undefined,
      props: undefined,
      title: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.SET_USER_TITLE,
      account: "gtg",
      title: "first-post",
      permlink: undefined,
      notes: undefined,
      props: undefined
    }
  }
}, {
  custom_json_operation: {
    accounts: [ "gtg" ],
    community: "mycomm",
    data: {
      action: ECommunityOperationActions.UPDATE_PROPS,
      props: {
        about: "",
        description: "",
        title: "Custom title",
        flag_text: "",
        is_nsfw: false,
        lang: "en",
      },
      account: undefined,
      permlink: undefined,
      notes: undefined,
      title: undefined
    }
  }
}]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

The formatted tree is plain JSON data — actions are their wire-form strings and absent optional fields are simply omitted (there is no `undefined` in `serde_json`).

:::code source="../../static/snippets/src/rust/formatters/operation_formatters/community.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/operation_formatters/community.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/operation_formatters/community.rs)" :::

==- Output

```json
[
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "flagPost",
        "notes": "note",
        "permlink": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "mutePost",
        "notes": "note",
        "permlink": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "pinPost",
        "permlink": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "action": "subscribe"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "unmutePost",
        "notes": "note",
        "permlink": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "unpinPost",
        "permlink": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "action": "unsubscribe"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "account": "gtg",
        "action": "setUserTitle",
        "title": "first-post"
      }
    }
  },
  {
    "custom_json_operation": {
      "accounts": ["gtg"],
      "community": "mycomm",
      "data": {
        "action": "updateProps",
        "props": {
          "about": "",
          "description": "",
          "flag_text": "",
          "is_nsfw": false,
          "lang": "en",
          "title": "Custom title"
        }
      }
    }
  }
]
```

===

+++

## Formatting follow operations

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/operation-formatters/follow.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/operation-formatters/follow.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Foperation-formatters%2Ffollow.ts&startScript=test-formatters-operation-formatters-follow)" :::

==- Output

```javascript
[{
  custom_json_operation: {
    action: EFollowActions.FOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.FOLLOW_MUTED,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.RESET_ALL_LISTS,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.RESET_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.RESET_FOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.RESET_FOLLOW_MUTED_LIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.UNBLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.UNFOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.UNFOLLOW,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json_operation: {
    action: EFollowActions.UNFOLLOW_MUTED,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json_operation: {
    account: "initminer",
    author: "gtg",
    permlink: "first-post"
  }
}]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

:::code source="../../static/snippets/src/rust/formatters/operation_formatters/follow.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/operation_formatters/follow.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/operation_formatters/follow.rs)" :::

==- Output

```json
[
  {
    "custom_json_operation": {
      "action": "follow_blacklist",
      "follower": "initminer",
      "following": ["gtg", "null"]
    }
  },
  {
    "custom_json_operation": {
      "action": "follow_muted",
      "follower": "initminer",
      "following": ["gtg"]
    }
  },
  {
    "custom_json_operation": {
      "action": "reset_all_lists",
      "follower": "initminer",
      "following": ["gtg", "null"]
    }
  },
  {
    "custom_json_operation": {
      "action": "reset_blacklist",
      "follower": "initminer",
      "following": ["gtg"]
    }
  },
  {
    "custom_json_operation": {
      "action": "reset_follow_blacklist",
      "follower": "initminer",
      "following": ["gtg", "null"]
    }
  },
  {
    "custom_json_operation": {
      "action": "reset_follow_muted_list",
      "follower": "initminer",
      "following": ["gtg"]
    }
  },
  {
    "custom_json_operation": {
      "action": "unblacklist",
      "follower": "initminer",
      "following": ["gtg", "null"]
    }
  },
  {
    "custom_json_operation": {
      "action": "unfollow_blacklist",
      "follower": "initminer",
      "following": ["gtg"]
    }
  },
  {
    "custom_json_operation": {
      "action": "",
      "follower": "initminer",
      "following": ["gtg", "null"]
    }
  },
  {
    "custom_json_operation": {
      "action": "unfollow_muted",
      "follower": "initminer",
      "following": ["gtg"]
    }
  },
  {
    "custom_json_operation": {
      "account": "initminer",
      "author": "gtg",
      "permlink": "first-post"
    }
  }
]
```

===

+++

## Formatting witness properties object

You can also parse the serialized [!badge variant="info" text="witness_set_properties"] operation - `props` property from the chain:

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/operation-formatters/witness-update.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/operation-formatters/witness-update.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Foperation-formatters%2Fwitness-update.ts&startScript=test-formatters-operation-formatters-witness-update)" :::

==- Output

```javascript
{
  key: 'STM5z76mjZJnTZHHZjgnFxFadTb1ztc6R7EuDgCzd6dNiv6ETB2tj',
  new_signing_key: 'STM2nf9tLEWSdisd5pjocs2odhD3PvsnJTfMmK7Gm2Z2x8CvpXs1WC',
  account_creation_fee: undefined,
  url: undefined,
  hbd_exchange_rate: undefined,
  maximum_block_size: undefined,
  hbd_interest_rate: undefined,
  account_subsidy_budget: undefined,
  account_subsidy_decay: undefined
}
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

Only the properties present in the packed `props` appear in the output (there is no `undefined` in `serde_json`).

:::code source="../../static/snippets/src/rust/formatters/operation_formatters/witness_update.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/operation_formatters/witness_update.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/operation_formatters/witness_update.rs)" :::

==- Output

```json
{
  "key": "STM5z76mjZJnTZHHZjgnFxFadTb1ztc6R7EuDgCzd6dNiv6ETB2tj",
  "new_signing_key": "STM2nf9tLEWSdisd5pjocs2odhD3PvsnJTfMmK7Gm2Z2x8CvpXs1WC"
}
```

===

+++
