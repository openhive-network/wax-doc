---
order: -2
icon: container
---

# Blockchain Data Formatters

## Formatting a large number

Using Wax Formatters, you can format numbers represented as `string`, `number`, `BigInt` and [`long`](https://www.npmjs.com/package/long) using `formatNumber` method

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-number.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-number.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-number.ts&startScript=test-formatters-blockchain-formatters-format-number)" :::

=== Output

```text
76,543,212,345,678.000
```

===

## Formatting NAI Asset

If you want to format a string, use `waxify` literal

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-nai.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-nai.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-nai.ts&startScript=test-formatters-blockchain-formatters-format-nai)" :::

=== Output

```text
Amount: 300.000 HIVE
```

===

## Formatting Transaction

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-tx.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-tx.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-tx.ts&startScript=test-formatters-blockchain-formatters-format-tx)" :::

=== Output

```text
Tx: #3725c81634f152011e2043eb7119911b953d4267
```

===

## Formatting entire transaction without replacing with transaction id

Sometimes there is a need to convert an entire transaction object, but you do not want it to be replaced with the string.
You can achieve that by using `format` method and extending the default Wax Formatter with your custom options, e.g.:

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-options.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-options.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-options.ts&startScript=test-formatters-blockchain-formatters-format-options)" :::

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
        amount: {
          amount: "300000",
          precision: 3,
          nai: "@@000000021"
        },
        memo: "Roll under 50 4d434bd943616"
      }
    }
  ],
  extensions: []
}
```

===
