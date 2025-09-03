---
order: -1
icon: comment
---

# Comment-reply and Post operations

One of the complex operations supported by the Hive blockchain is the publishing of blog posts and replies (comments) to them. To simplify it, the Wax library provides specific helper operation factory classes: Blog Post Operation and Reply Operation. Below, we provide snippets for creating blog posts and replies including scenarios where additional properties are defined. These scenarios internally involve an additional blockchain operation called [!badge variant="info" text="comment_options_operation"].

!!!secondary
This complex operations generate [!badge variant="info" text="comment_options_operation"] only if user provided values different from the defaults.
!!!

## Creating a blog post with custom JSON-metadata properties

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/comment/creating-article.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/comment/creating-article.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Fcomment%2Fcreating-article.ts&startScript=test-transaction-operations-creating-article)" :::

+++ Python

TBA

+++

## Creating a Comment (Reply) with multiple JSON-metadata attributes

You can set multiple properties on one operation class instance, as shown in the example below.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/comment/creating-reply.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/comment/creating-reply.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Fcomment%2Fcreating-reply.ts&startScript=test-transaction-operations-creating-reply)" :::

+++ Python

TBA

+++
