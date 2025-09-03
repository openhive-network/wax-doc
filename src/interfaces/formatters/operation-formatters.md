---
order: -3
icon: tasklist
---

# Operation Formatters

## Formatting RC delegation operations

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

## Formatting community operations

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

## Formatting follow operations

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

## Formatting witness properties object

You can also parse the serialized [!badge variant="info" text="witness_set_properties"] operation - `props` property from the chain:

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
