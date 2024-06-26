---
order: -2
icon: container
---

# Blockchain Data Formatters

## Formatting a large number

Using Wax Formatters, you can format numbers represented as `string`, `number`, `BigInt` and [`long`](https://www.npmjs.com/package/long) using `formatNumber` method

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

const output = chain.formatter.formatNumber(76543212345678, 3, "en-US");

console.log(output);
```

=== Output

```text
76,543,212,345,678.000
```

===

## Formatting NAI Asset

If you want to format a string, use `waxify` literal

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

// Data from blockchain
const naiAsset = {
  amount: "300000",
  precision: 3,
  nai: "@@000000021"
};

const output = chain.waxify`Amount: ${naiAsset}`;

console.log(output);
```

=== Output

```text
Amount: 300.000 HIVE
```

===

## Formatting Transaction

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

// Data from blockchain
const tx = {
  ref_block_num: 1959,
  ref_block_prefix: 3625727107,
  expiration: "2023-11-09T22:01:24",
  operations: [
    {
      type: "transfer_operation",
      value: {
        from: "oneplus7",
        to: "kryptogames",
        amount: naiAsset,
        memo: "Roll under 50 4d434bd943616"
      }
    }
  ],
  extensions: []
};

const output = chain.waxify`Tx: #${tx}`;

console.log(output);
```

=== Output

```text
Tx: #3725c81634f152011e2043eb7119911b953d4267
```

===

## Formatting entire transaction without replacing with transaction id

Sometimes there is a need to convert an entire transaction object, but you do not want it to be replaced with the string.
You can achieve that by using `format` method and extending the default Wax Formatter with your custom options, e.g.:

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

// Data from blockchain
const tx = {
  ref_block_num: 1959,
  ref_block_prefix: 3625727107,
  expiration: "2023-11-09T22:01:24",
  operations: [
    {
      type: "transfer_operation",
      value: {
        from: "oneplus7",
        to: "kryptogames",
        amount: naiAsset,
        memo: "Roll under 50 4d434bd943616"
      }
    }
  ],
  extensions: []
};

const formatter = chain.formatter.extend({ transaction: { displayAsId: false } });

const output = formatter.format(tx);

console.log(output);
```

==- Output

```javascript
{
  ref_block_num: 1959,
  ref_block_prefix: 3625727107,
  expiration: "2023-11-09T22:01:24",
  operations: [
    {
      type: "transfer_operation",
      value: {
        from: "oneplus7",
        to: "kryptogames",
        amount: naiAsset,
        memo: "Roll under 50 4d434bd943616"
      }
    }
  ],
  extensions: []
}
```

===
