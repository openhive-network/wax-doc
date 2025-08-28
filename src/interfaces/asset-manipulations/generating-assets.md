---
order: -2
icon: law
---

# Generating Assets

There are two primary methods to generate `hive`, `vests`, or `hbd`, categorized based on the type of input they accept.

## Coins Functions

These functions are designed to handle floating-point numbers using JavaScript's double-precision floating-point format (IEEE 754). They can accept fractional values but are limited to numbers within JavaScript's precision bounds (i.e., not exceeding `2^53 - 1` or below `-(2^53 - 1)`).

+++ JavaScript

```ts
// Example:
chain.hiveCoins(100.3) // {"amount":"100300","precision":3,"nai":"@@000000021"}

/* Note that the fractional parts have been extended with implicit zeros, making it equivalent to providing 100.300 as the amount! */

chain.hbdCoins(100).amount // 100000

/* Note that the fractional parts have been extended with implicit zeros, making it equivalent to providing 100.000 as the amount! */
```

+++ Python

TBA

+++

!!!secondary **Fractional parts note**
Please be mindful of the maximum fractional parts that each asset can accept: 3 for `hive` and `hbd`, and 6 for `vests`.

If you provide fewer fractional parts than the asset can accept, they will be extended with implicit zeros, making it equivalent to providing the maximum number of fractional parts, as shown in the example above.

If you provide more fractional parts than the asset can accept, they will be cut to the acceptable precision, as shown in the example below.
!!!

+++ JavaScript

```ts
// Example of exceeding the precision limit for fractional parts:
chain.hiveCoins(100.123456).amount // 100123 - the rest of the fractional parts have been cut without any rounding down.

chain.hbdCoins(100.123678).amount // 100123 - the rest of the fractional parts have been cut without any rounding up.

chain.vestsCoins(100.123456789).amount // 100123456 - the rest of the fractional parts have just been cut.
```

+++ Python

TBA

+++

## Satoshis Functions

These functions accept only integer values and do not perform any conversion on the input, other than adding a NaiAsset ID. They are capable of handling very large integers, supported by BigInt and large string representations of numbers.

+++ JavaScript

```ts
// Example:
chain.hiveSatoshis(100) // {"amount":"100","precision":3,"nai":"@@000000021"}
```

+++ Python

TBA

+++

## `coins` vs `satoshis`

When choosing the appropriate function to generate an amount, consider the input type. Use the `satoshis` methods for large integer values. For floating-point numbers, choose the `coins` methods. It's preferable to use `coins` when working with scripts containing known, hardcoded amounts, while `satoshis` is better suited for API interactions or when amounts are provided by a user.
