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

TODO: Code

## Adding account to the posting role

TODO: Code

## Changing active key

TODO: Code

## Modifying the owner level with treshold change

TODO: Code

## Iterating over the hive category roles

TODO: Code
