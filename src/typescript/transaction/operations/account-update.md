---
order: -5
icon: repo-locked
---

# Account authority update

Another complex operation supported by the Hive blockchain is updating your account authority. We made it simple by creating an universal abstract interface for all of the current and future role categories.

!!!warning
We currently support only the `hive` role category.
!!!

## Online operations

Account authority update operation is one of the "Online operations", which initially require online access to the live blockchain in order to work.

We have to parse your current authority data in order to create a new, valid authority object.

## Role categories and levels concept

Role category is a container for given set of role levels.

Role category can describe authorities saved as custom JSONs, comment JSON metadata, user metadata or base `hive` authorities. Role category can be a set of authorities used in, for example: your on-blockchain game or service.

In given role category you can create multiple levels of authorities. Given the base `hive` role category, we have 4 base levels - `active`, `posting`, `owner` and `memo`.

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
