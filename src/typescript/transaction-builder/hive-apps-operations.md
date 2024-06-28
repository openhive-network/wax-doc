---
order: -5
icon: tasklist
label: HiveApps Operations
---

# HiveApps Operations in Transaction Builder

The Hive blockchain enables advanced operations using `custom_json`. These operations are standardized and recognized by the Hive ecosystem, such as Hivemind. This allows us to utilize advanced features that go beyond typical Hive blockchain operations. These custom operations are known as HiveApps operations.

## What is a HiveApps Operation?

A HiveApps operation is essentially a `custom_json` operation. Through these operations, we can execute custom actions on the Hive blockchain which are recognized and processed by the Hive infrastructure, like Hivemind.

## HiveApps Operations Builders

To facilitate the construction and management of these operations, we use the `HiveAppsOperationsBuilder`. Below are specific builders for different types of HiveApps operations:

### 1. ResourceCreditsOperationBuilder

This builder is used to manage Resource Credits (RC) delegations. Resource Credits allow actions to be performed on the Hive blockchain without paying transaction fees.

#### Example usage:

If you want to help a friend perform more operations on their account, you can delegate some of your Resource Credits to them.
Meanwhile the other friends does not need your help anymore, so you can remove the delegation.

:::code source="../../static/snippets/src/typescript/transaction-builder/hive-apps-operations/resource-credits-operations.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/hive-apps-operations/resource-credits-operations.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fhive-apps-operations%2Fresource-credits-operations.ts&startScript=test-tb-hive-apps-resource-credits)" :::

==- Output

```javascript
[
  // Delegate
  {
    custom_json: {
      id: 'rc',
      json: '["delegate_rc",{"from":"your_account","delegatees":["your_friend_account"],"max_rc":"1000","extensions":[]}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  },
  // Remove delegation
  {
    custom_json: {
      id: 'rc',
      json: '["delegate_rc",{"from":"your_account","delegatees":["other_friend_account"],"max_rc":"0","extensions":[]}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  }
]
```

```text
Required posting auths: your_account
```
===

### 2. FollowOperationBuilder

This builder handles operations related to following, muting, blacklisting blogs, and reblogging posts.

#### Example usage:

Here is an example of complex `FollowOperationBuilder` usage:

:::code source="../../static/snippets/src/typescript/transaction-builder/hive-apps-operations/follow-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/hive-apps-operations/follow-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fhive-apps-operations%2Ffollow-operation.ts&startScript=test-tb-hive-apps-follow-operation)" :::

==- Output

```javascript
[
  // Follow blog
  {
    custom_json: {
      id: 'follow',
      json: '["follow",{"follower":"your_account","following":"interesting_blog","what":["blog"]}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  },
  // Mute blog
  {
    custom_json: {
      id: 'follow',
      json: '["follow",{"follower":"your_account","following":"spammer","what":["ignore"]}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  },
  // Reblog
  {
    custom_json: {
      id: 'follow',
      json: '["reblog",{"account":"your_account","author":"reblog_me","permlink":"post_permlink"}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  }
]
```
```text
Required posting auths: your_account
```
===

### 3. CommunityOperationBuilder

This builder manages operations specific to communities on the Hive blockchain.

#### Example Usage:

##### Community member:

You want to join a specific community to stay updated with its content and you want flag some post. Here is an example how you can do it:

:::code source="../../static/snippets/src/typescript/transaction-builder/hive-apps-operations/community-operation.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/hive-apps-operations/community-operation.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fhive-apps-operations%2Fcommunity-operation.ts&startScript=test-tb-hive-apps-community-operation)" :::

==- Output

```javascript
[
  // Subscribe
  {
    custom_json: {
      id: 'community',
      json: '["subscribe",{"community":"community_name"}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  },
  // Flag post
  {
    custom_json: {
      id: 'community',
      json: '["flagPost",{"community":"community_name","account":"author_account","permlink":"post_permlink","notes":"violation notes"}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  }
]
```
```text
Required posting auths: your_account
```
===

##### Updating Community Properties:

Since you are an community administrator, you can update its properties:

:::code source="../../static/snippets/src/typescript/transaction-builder/hive-apps-operations/community-properties.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/hive-apps-operations/community-properties.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fhive-apps-operations%2Fcommunity-properties.ts&startScript=test-tb-hive-apps-community-properties)" :::

==- Output

```javascript
[
  {
    custom_json: {
      id: 'community',
      json: '["updateProps",{"community":"community_name","props":{"title":"New Community Title","about":"Community Description","description":"Detailed community description","flag_text":"Post flagging rules","is_nsfw":false,"lang":"en"}}]',
      required_auths: [],
      required_posting_auths: [Array]
    }
  }
]
```
```text
Required posting auths: your_account
```
===

!!!warning Authorize operations
**Remember to always authorize your operations.** The account that authorizes the operation also **must sign the transaction** (as shown in the first example).
!!!

## Summary

HiveApps operations enable the execution of complex tasks on the Hive blockchain using `custom_json`. By utilizing the appropriate builders, users and developers can efficiently create, manage, and authorize these operations, ensuring smooth and standardized interactions in the Hive ecosystem. This simplifies and automates the management of communities, resource credits, and subscriptions.