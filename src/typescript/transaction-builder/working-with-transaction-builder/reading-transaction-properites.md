---
order: -3
icon: book
label: Reading properites
---

# Reading transaction properites

The `TransactionBuilder` interface also allows you to read your transaction properties like `sig_digest`, `id`, etc.

:::code source="../../../static/snippets/src/typescript/transaction-builder/working-with-tb/reading-properties/reading-properties.ts" language="typescript" title="Test it yourself: [src/typescript/transaction-builder/working-with-tb/reading-properties/reading-properties.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction-builder%2Fworking-with-tb%2Freading-properties%2Freading-properties.ts&startScript=test-tb-working-with-tb-reading-properties)" :::

=== Output

```text
id: 7546920767a3ec6ee6555f07e23d2f295ee77c7f
sigDigest: e25a352f97d92247bfc56b2420beeb7c0ccfe5ea9fac5180ea27c3d7e15d5540
expiration: 2024-06-27T11:32:16
ref_block_num: 1960
```

===
