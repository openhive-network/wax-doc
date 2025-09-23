---
order: -5
icon: repo-locked
---

# Account authority update

Another troublesome operation offered by Hive Blockchain is [!badge variant="info" text="account_update2_operation"] dedicated to changing account authority. To simplify blockchain implementation, this operation must contain a whole authority role specification (for the `owner`, `active`, `posting` roles), because it overwrites it in the blockchain account representation.
So missing some part of current authority definitions leads to dramatic scenarios when account authority definition can be broken.
To simplify this process, wax library offers Account Authority Update meta operation which is responsible for collecting initial set of authority definitions and next allows to modify them by adding/removing/replacing authority entries.

Another important feature of this operation is tracking changes in the authority objects. Actual blockchain operation will be generated only if the authority object has been effectively changed according to initially loaded state.

To prevent errors when actual generation is skipped, the Account Authority Update class offers `isEffective` property, which allows the caller to determine if any further transaction processing is needed.

UI developers can be also interested in direct use of the Account Authority Update operation as their intermediate data storage specific to UI, because:

- it offers a way to iterate over the authority objects and display them in a user-friendly way (needed to initially supply the view)
- provides basic editing capabilities by mentioned above entry specific methods (`add/replace/remove/reset`), like also additional `reset()` method being useful for canceling changes in the authority editor view.
- allows to determine data modification state by `isEffective` property, what can be useful in displaying a dirty state in the view

## Online operations

Account authority update operation is one of the "Online operations", which initially require online access to the live blockchain in order to work.

We have to parse your current authority data in order to create a new, valid authority object.

## Role categories and levels concept

Role category is a container for given set of role levels. The idea behind it, is to leave an open way for creating another role categories definitions in the future, once Hive Blockchain will support them. Thus, even set of role categories evolves, you can still use the same Account Authority Update class to manage them.

Role category can describe authorities saved as custom JSONs, comment JSON metadata, user metadata or base `hive` authorities. Role category can be a set of authorities used in, for example: your on-blockchain game or service.

In given role category you can create multiple levels of authorities. Given the base `hive` role category, we have 4 base levels - `active`, `posting`, `owner` and `memo`.

!!!warning
We currently support only the `hive` role category.
!!!

## Setting new memo key on the profile

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/set-memo.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/set-memo.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fset-memo.ts&startScript=test-transaction-operations-account-update-set-memo)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/account_update/set_memo.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/account_update/set_memo.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/operations/account_update/set_memo.py)" :::

+++

## Adding account proxy to the posting role definition

Sometimes you want to allow a separate account to operate on behalf of your account (e.g., a bot, backup account, or trusted service). To define such authority proxy, you can use the `AccountAuthorityUpdateOperation` by calling its `add(account: TAccountName, weight: number = 1)` method. The important aspect is matching the account weight to the role threshold - only entries with weights equal or greater than the role threshold will be able to authorize operations and satisfy the authority.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/add-posting-account.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/add-posting-account.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fadd-posting-account.ts&startScript=test-transaction-operations-account-update-add-posting-account)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/account_update/add_posting_account.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/account_update/add_posting_account.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/operations/account_update/add_posting_account.py)" :::

+++

## Changing active key

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/change-active-key.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/change-active-key.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fchange-active-key.ts&startScript=test-transaction-operations-account-update-change-active-key)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/account_update/change_active_key.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/account_update/change_active_key.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/operations/account_update/change_active_key.py)" :::

+++

## Modifying the owner level with threshold change

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/change-weight-threshold.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/change-weight-threshold.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fchange-weight-threshold.ts&startScript=test-transaction-operations-account-update-change-weight-threshold)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/account_update/change_weight_threshold.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/account_update/change_weight_threshold.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/operations/account_update/change_weight_threshold.py)" :::

+++

## Iterating over the hive category roles

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/operations/account-update/iterate-roles.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/operations/account-update/iterate-roles.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Foperations%2Faccount-update%2Fiterate-roles.ts&startScript=test-transaction-operations-account-update-iterate-roles)" :::

+++ Python

:::code source="../../../static/snippets/src/python/transaction/operations/account_update/iterate_roles.py" language="python" title="Test it yourself on github codespace: [src/python/transaction/operations/account_update/iterate_roles.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/transaction/operations/account_update/iterate_roles.py)" :::

+++
