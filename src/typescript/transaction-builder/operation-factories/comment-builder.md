---
order: -1
icon: comment
---

# Using Comment-reply and Post factory

The `CommentBuilder` class within the Wax library allows you to create and manage comment operations on the Hive blockchain. Below, we provide snippets for creating comments and replies with both default and explicit values.

## Creating a Comment with Basic Values and Description

```typescript
import { createHiveChain, ArticleBuilder, ReplyBuilder } from '@hiveio/wax';

// Initialize the chain
const chain = await createHiveChain();

// Create a transaction
const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

/**
 * Uses the operation builder on the transaction and specifies two arguments:
 * 1. The builder you would like to use,
 * 2. Arrow function to use specific methods that are available inside the builder you have chosen.
 */
tx.useBuilder(ArticleBuilder, builder => {
    builder.setDescription('This is the description of the post inside ArticleBuilder');
}, 'parent_author', 'parent_permlink', 'author', 'body');

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
tx.build();
```

## Creating a Comment with Multiple Explicit Values

You can use multiple values on one builder instance, as shown in the example below.

```typescript
import { createHiveChain, ReplyBuilder } from '@hiveio/wax';

// Initialize the chain
const chain = await createHiveChain();

// Create a transaction
const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

// Use multiple explicit values
tx.useBuilder(ReplyBuilder, builder => {
    builder
        .setDescription('This is the description of the post inside ReplyBuilder')
        .pushTags('hive')
        .addBeneficiaries({ account: 'test-account', weight: 40 });
}, 'parent_author', 'parent_permlink', 'author', 'body');

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
tx.build();
```