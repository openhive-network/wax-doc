---
order: -3
icon: tasklist
---

# Operation Formatters

## Formatting RC delegation operations

```typescript
import { createHiveChain, ResourceCreditsOperationBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.getTransactionBuilder();

tx.push(new ResourceCreditsOperationBuilder()
  .delegate("initminer", 4127361273, "gtg", "null")
  .removeDelegation("initminer", "null")
  .authorize("initminer")
  .build());

const built = tx.build();

const output = chain.formatter.format(built.operations);

console.log(output);
```

==- Output

```javascript
[{
  custom_json: {
    delegatees: [ "gtg", "null" ],
    from: "initminer",
    rc: {
      amount: "4127361273",
      nai: "@@000000037",
      precision: 6,
    }
  }
}, {
  custom_json: {
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

```typescript
import { createHiveChain, CommunityOperationBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.getTransactionBuilder();

tx.push(new CommunityOperationBuilder()
  .flagPost("mycomm", "gtg", "first-post", "note")
  .mutePost("mycomm", "gtg", "first-post", "note")
  .pinPost("mycomm", "gtg", "first-post")
  .subscribe("mycomm")
  .unmutePost("mycomm", "gtg", "first-post", "note")
  .unpinPost("mycomm", "gtg", "first-post")
  .unsubscribe("mycomm")
  .setUserTitle("mycomm", "gtg", "first-post")
  .updateProps("mycomm", { title: "Custom title" })
  .authorize("gtg")
  .build());

const built = tx.build();

const output = chain.formatter.format(built.operations);

console.log(output);
```

==- Output

```javascript
[{
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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
  custom_json: {
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

```typescript
import { createHiveChain, FollowOperationBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.getTransactionBuilder();

tx.push(new FollowOperationBuilder()
  .followBlacklistBlog("initminer", "gtg", "null")
  .followMutedBlog("initminer", "gtg")
  .resetAllBlog("initminer", "gtg", "null")
  .resetBlacklistBlog("initminer", "gtg")
  .resetFollowBlacklistBlog("initminer", "gtg", "null")
  .resetFollowMutedBlog("initminer", "gtg")
  .unblacklistBlog("initminer", "gtg", "null")
  .unfollowBlacklistBlog("initminer", "gtg")
  .unfollowBlog("initminer", "gtg", "null")
  .unfollowMutedBlog("initminer", "gtg")
  .reblog("initminer", "gtg", "first-post")
  .authorize("initminer")
  .build());

const built = tx.build();

const output = chain.formatter.format(built.operations);

console.log(output);
```

==- Output

```javascript
[{
  custom_json: {
    action: EFollowActions.FOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.FOLLOW_MUTED,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.RESET_ALL_LISTS,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.RESET_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.RESET_FOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.RESET_FOLLOW_MUTED_LIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.UNBLACKLIST,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.UNFOLLOW_BLACKLIST,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.UNFOLLOW,
    follower: "initminer",
    following: [
      "gtg",
      "null"
    ]
  }
}, {
  custom_json: {
    action: EFollowActions.UNFOLLOW_MUTED,
    follower: "initminer",
    following: [
      "gtg"
    ]
  }
}, {
  custom_json: {
    account: "initminer",
    author: "gtg",
    permlink: "first-post"
  }
}]
```

===

## Formatting witness properties object

You can also parse the serialized [!badge variant="info" text="witness_set_properties"] operation - `props` property from the chain:

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

// Data from blockchain
const witness_props = {
  type: "witness_set_properties_operation",
  value: {
    owner: "null",
    props: [
      ["new_signing_key","3553544d365471534a61533161526a367036795a456f35786963583762764c6872666456716935546f4e724b78485533465242456457"],
      ["key", "029072da2e84ebd6eb520f944db3d1af718500b0f1ddf60e11e986f990acddd524"]
    ],
    extensions: []
  }
};

const output = chain.formatter.format(witness_props);

console.log(output.value.props);
```

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
