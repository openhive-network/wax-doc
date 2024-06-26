---
order: -1
icon: comment
---

# Comment-reply and Post factories

One of complex operations supported by Hive blockchain is publishing the posts (articles) and replies (comments) to them. To simplify it, the Wax library provides two helper operation factory classes: `ArticleBuilder` and `ReplyBuilder`. Below, we provide snippets for creating post and reply including scenarios when are defined additional properties, (internally) involving additionally another blockchain operation: `comment_options_operation`.

## Creating an article with custom JSON-metadata properties

```typescript
import { createHiveChain, ArticleBuilder } from '@hiveio/wax';

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
    // Here you can set standard set of JSON-metadata properties, supported by Hive-Apps stack
    builder.setDescription('This is the description of the post inside ArticleBuilder')
      .setAlternativeAuthor('Ernest Hemingway')
      .setCategory('literature')
      .addBeneficiaries({ account: 'conan-librarian', weight: 40 });
      ;
    ;
  },
  // Here you can pass the arguments to given builder class constructor: author, title and body.
  // Permlink specification can be skipped - the library will generate the one for you basing on author and current time to enforce uniqueness.
  'post_author', 'post-title', 'the-post-body'
);

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
tx.build();
```

## Creating a Comment (Reply) with multiple JSON-metadata attributes

You can set multiple properties on one builder instance, as shown in the example below.

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
        .pushTags('hive');
  },
  // Here `parentAuthor` and `parentPermlink` arguments can't be skipped nor be empty.
  // Also other required operation basic attributes (like `author`) must be explicitly specified.
  'parent_author', 'parent_permlink', 'reply_author', 'reply-body'
);

// Build up ProtoTransaction object holding all operations and transaction TAPOS & expiration data, but transaction is **not signed yet**
tx.build();
```
