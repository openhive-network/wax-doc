---
order: -2
icon: law
---

# Generating Assets

There are two primary methods to generate `hive`, `vests`, or `hbd`, categorized based on the type of input they accept.

## Coins Functions

These functions are designed to handle floating-point numbers using JavaScript's double-precision floating-point format (IEEE 754). They can accept fractional values but are limited to numbers within JavaScript's precision bounds (i.e., not exceeding `2^53 - 1` or below `-(2^53 - 1)`).

```ts
// Example:
chain.hiveCoins(100.3) // {"amount":"100300","precision":3,"nai":"@@000000021"}
```

!!!secondary Note
Please be mindful of the maximum fractional parts that each asset can accept: 3 for `hive` and `hbd`, and 6 for `vests`.
!!!

## Satoshis Functions

These functions accept only integer values and do not perform any conversion on the input, other than adding a NaiAsset ID. They are capable of handling very large integers, supported by BigInt and large string representations of numbers.

```ts
// Example:
chain.hiveSatoshis(10000000000000000) // {"amount":"10000000000000000000","precision":3,"nai":"@@000000021"}
```

## `coins` vs `satoshis`

When choosing the appropriate function to generate an amount, consider the input type. Use the `satoshis` methods for large integer values. For floating-point numbers, choose the `coins` methods. It's preferable to use `coins` when working with scripts containing known, hardcoded amounts, while `satoshis` is better suited for API interactions or when amounts are provided by a user.
