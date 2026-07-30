---
order: -2
icon: container
---

# Blockchain Data Formatters

## Formatting a large number

Using Wax Formatters, you can format numbers represented as `string`, `number`, `BigInt` using `formatNumber` method

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-number.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-number.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-number.ts&startScript=test-formatters-blockchain-formatters-format-number)" :::

=== Output

```text
76,543,212,345,678.000
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

`format_number` accepts any amount convertible to a string (integers, floats, decimal strings). There is no locale argument — group separators default to the `en-US` style and can be changed with `WaxFormatterOptions::default().with_separators(...)`.

:::code source="../../static/snippets/src/rust/formatters/blockchain_formatters/format_number.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/blockchain_formatters/format_number.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/blockchain_formatters/format_number.rs)" :::

=== Output

```text
76,543,212,345,678.000
```

===

+++

## Formatting NAI Asset

If you want to format a string, use `waxify` literal

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-nai.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-nai.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-nai.ts&startScript=test-formatters-blockchain-formatters-format-nai)" :::

=== Output

```text
Amount: 300.000 HIVE
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

Rust has no tagged template literals — `display` is the counterpart of `waxify`: it formats the value and renders it for display, ready to be composed with the `format!` family.

:::code source="../../static/snippets/src/rust/formatters/blockchain_formatters/format_nai.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/blockchain_formatters/format_nai.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/blockchain_formatters/format_nai.rs)" :::

=== Output

```text
Amount: 300.000 HIVE
```

===

+++

## Formatting Transaction

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/blockchain-formatters/format-tx.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/blockchain-formatters/format-tx.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fblockchain-formatters%2Fformat-tx.ts&startScript=test-formatters-blockchain-formatters-format-tx)" :::

=== Output

```text
Tx: #3725c81634f152011e2043eb7119911b953d4267
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

:::code source="../../static/snippets/src/rust/formatters/blockchain_formatters/format_tx.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/blockchain_formatters/format_tx.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/blockchain_formatters/format_tx.rs)" :::

=== Output

```text
Tx: #3725c81634f152011e2043eb7119911b953d4267
```

===

+++

## Formatting entire transaction without replacing with transaction id

Sometimes there is a need to convert an entire transaction object, but you do not want it to be replaced with the string.
You can achieve that by using `format` method and extending the default Wax Formatter with your custom options, e.g.:

+++ JavaScript

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

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

In Rust the options-only extension is a separate method: `extend_options` derives a new formatter with the same rules but the given options (`extend::<F>()` is the rule-extension form). `format` returns the rewritten tree as plain `serde_json::Value` data.

:::code source="../../static/snippets/src/rust/formatters/blockchain_formatters/format_options.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/blockchain_formatters/format_options.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/blockchain_formatters/format_options.rs)" :::

==- Output

```json
{
  "expiration": "2023-11-09T22:01:24",
  "extensions": [],
  "operations": [
    {
      "type": "transfer_operation",
      "value": {
        "amount": "300.000 HIVE",
        "from": "oneplus7",
        "memo": "Roll under 50 4d434bd943616",
        "to": "kryptogames"
      }
    }
  ],
  "ref_block_num": 1959,
  "ref_block_prefix": 3625727107
}
```

===

+++
