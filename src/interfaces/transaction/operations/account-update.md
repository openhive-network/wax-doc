---
order: -5
icon: repo-locked
---

# Account authority update

Another troublesome operation offered by Hive Blockchain is `account_update2_operation` dedicated to changing account authority. To simplify blockchain implementation, this operation must contain a whole authority role specification (for the `owner`, `active`, `posting` roles), because it overwrites it in the blockchain account representation.
So missing some part of current authority definitions leads to dramatic scenarios when account authority definition can be broken.
To simplify this process, wax library offers `AccountAuthorityUpdate` meta operation which is responsible for collecting initial set of authority definitions and next allows to modify them by adding/removing/replacing authority entries.

Another important feature of this operation is tracking changes in the authority objects. Actual blockchain operation will be generated only if the authority object has been effectively changed according to initially loaded state.

To prevent errors when actual generation is skipped, the `AccountAuthorityUpdate` class offers `isEffective` property, which allows the caller to determine if any further transaction processing is needed.

UI developers can be also interested in direct use of the `AccountAuthorityUpdate` operation as their intermediate data storage specific to UI, because:
- it offers a way to iterate over the authority objects and display them in a user-friendly way (needed to initially supply the view)
- provides basic editing capabilities by mentioned above entry specific methods (`add/replace/remove/reset`), like also additional `reset()` method being useful for canceling changes in the authority editor view.
- allows to determine data modification state by `isEffective` property, what can be useful in displaying a dirty state in the view

## Online operations

Account authority update operation is one of the "Online operations", which initially require online access to the live blockchain in order to work.

We have to parse your current authority data in order to create a new, valid authority object.

## Role categories and levels concept

Role category is a container for given set of role levels. The idea behind it, is to leave an open way for creating another role categories definitions in the future, once Hive Blockchain will support them. Thus, even set of role categories evolves, you can still use the same `AccountAuthorityUpdate` class to manage them.

Role category can describe authorities saved as custom JSONs, comment JSON metadata, user metadata or base `hive` authorities. Role category can be a set of authorities used in, for example: your on-blockchain game or service.

In given role category you can create multiple levels of authorities. Given the base `hive` role category, we have 4 base levels - `active`, `posting`, `owner` and `memo`.

!!!warning
We currently support only the `hive` role category.
!!!

## Setting new memo key on the profile

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/set-memo.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/set-memo.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fset-memo.ts&startScript=test-transaction-operations-account-update-set-memo)" :::

## Adding account to the posting role

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/add-posting-account.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/add-posting-account.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fadd-posting-account.ts&startScript=test-transaction-operations-account-update-add-posting-account)" :::

## Changing active key

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/change-active-key.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/change-active-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fchange-active-key.ts&startScript=test-transaction-operations-account-update-change-active-key)" :::

## Modifying the owner level with treshold change

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/change-weight-treshold.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/change-weight-treshold.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fchange-weight-treshold.ts&startScript=test-transaction-operations-account-update-change-weight-treshold)" :::

## Iterating over the hive category roles

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/iterate-roles.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/iterate-roles.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fiterate-roles.ts&startScript=test-transaction-operations-account-update-iterate-roles)" :::
