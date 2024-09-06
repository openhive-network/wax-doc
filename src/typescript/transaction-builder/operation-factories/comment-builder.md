---
order: -1
icon: comment
---

# Comment-reply and Post operations

One of complex operations supported by Hive blockchain is publishing the blog posts and replies (comments) to them. To simplify it, the Wax library provides two helper operation factory classes: `BlogPostOperation` and `ReplyOperation`. Below, we provide snippets for creating blog post and reply including scenarios when are defined additional properties, (internally) involving additionally another blockchain operation: `comment_options_operation`.

## Creating aa blog post with custom JSON-metadata properties

:::code source="../../../static/snippets/src/typescript/transaction-builder/operation-factories/comment-builder/creating-article.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/operation-factories/comment-builder/creating-article.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Foperation-factories%2Fcomment-builder%2Fcreating-article.ts&startScript=test-tb-operation-factories-creating-article)" :::

## Creating a Comment (Reply) with multiple JSON-metadata attributes

You can set multiple properties on one operation class instance, as shown in the example below.

:::code source="../../../static/snippets/src/typescript/transaction-builder/operation-factories/comment-builder/creating-reply.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/operation-factories/comment-builder/creating-reply.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Foperation-factories%2Fcomment-builder%2Fcreating-reply.ts&startScript=test-tb-operation-factories-creating-reply)" :::
