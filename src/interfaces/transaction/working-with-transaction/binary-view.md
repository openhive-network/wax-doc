---
order: -5
icon: codescan
label: Binary view
---

# Binary representation of transaction

The `ITransaction` interface also supports conversion to and from binary formats. This means you can easily serialize and deserialize transaction objects for efficient storage or deep analysis.

## Overview

The `ITransaction` interface provides methods for:

- Serializing transaction objects to binary format
- Serializing transaction objects to binary metadata format, describing their structure and fields
- Deserializing binary data back into transaction objects

Thanks to those capabilities, we were able to create the Binary View Component (available through the [Transaction Inspector app](https://tx.openhive.network)):

![Binary view UI](../../../static/binary-view.jpg)

## What is Binary Format

The binary format of a transaction is a compact, serialized byte representation of all transaction data following Hive's binary serialization protocol. This format:

- Represents all transaction fields and operations in a compact binary form
- Is used internally by Hive nodes for transaction processing and blockchain storage
- Provides a more network-efficient way to transmit transactions compared to JSON
- Serves as the canonical format for transaction signature generation
- Contains fixed-length and variable-length fields according to Hive's binary serialization rules

Understanding binary format is essential when working with transaction signatures, blockchain explorers, and low-level Hive tools.

## HF26 and Legacy Format Considerations

Hive implemented significant changes to the transaction format in Hardfork 26 (HF26). This affects binary serialization in the following ways:

- **Pre-HF26 (Legacy)**: Operations are serialized as paired arrays `["optype", {...params}]`
- **Post-HF26 (Modern)**: Operations are serialized as objects with type and value fields `{type: "optype_operation", value: {...params}}`

When working with binary transactions, you must be aware of which format is expected by the tools or nodes you're interacting with. The WAX library provides methods for both formats:

- `toBinaryForm()` - Returns the modern binary format
- There are also considerations when calculating transaction digests for signing (see below)

!!!secondary Impact on Signatures
The binary format directly impacts transaction signatures because signatures are calculated based on the transaction digest (hash of binary data).
!!!

## Conversion to binary format

With this conversion method, you can decide to strip to the unsigned transaction, which removes any information about the signatures container (by default the signatures container is present):

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/binary-view/to-binary.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/binary-view/to-binary.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Fbinary-view%2Fto-binary.ts&startScript=test-transaction-working-with-transaction-binary-to)" :::

=== Output

```javascript
"8059b32ca6018b9fb568010003677467036774670b68656c6c6f2d776f726c6498080000"
```

===

+++ Python

TBA

+++

## Retrieving transaction binary metadata

You can also retrieve the binary metadata, which in details describes the structure and fields of the transaction, along their size and offset in bytes:

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/binary-view/get-binary-metadata.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/binary-view/get-binary-metadata.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Fbinary-view%2Fget-binary-metadata.ts&startScript=test-transaction-working-with-transaction-binary-metadata)" :::

==- Output

```javascript
{
  binary: '995a8f30236ddba2b568010003677467036774670b68656c6c6f2d776f726c6498080000',
  offsets: [
    {
      key: 'ref_block_num',
      type: 'scalar',
      offset: 0,
      size: 2,
      value: '23193',
      length: undefined,
      children: undefined
    },
    {
      key: 'ref_block_prefix',
      type: 'scalar',
      offset: 2,
      size: 4,
      value: '1831022735',
      length: undefined,
      children: undefined
    },
    {
      key: 'expiration',
      type: 'scalar',
      offset: 6,
      size: 4,
      value: '2025-09-01T13:42:51',
      length: undefined,
      children: undefined
    },
    {
      key: 'operations',
      type: 'array',
      offset: 10,
      size: 24,
      value: 'Length: 1',
      length: 1,
      children: [
        {
          key: '0',
          type: 'object',
          offset: 11,
          size: 23,
          value: undefined,
          length: undefined,
          children: [
            {
              key: 'type',
              type: 'scalar',
              offset: 11,
              size: 1,
              value: 'vote_operation',
              length: undefined,
              children: undefined
            },
            {
              key: 'value',
              type: 'object',
              offset: 12,
              size: 22,
              value: undefined,
              length: undefined,
              children: [
                {
                  key: 'voter',
                  type: 'scalar',
                  offset: 12,
                  size: 4,
                  value: 'gtg',
                  length: undefined,
                  children: undefined
                },
                {
                  key: 'author',
                  type: 'scalar',
                  offset: 16,
                  size: 4,
                  value: 'gtg',
                  length: undefined,
                  children: undefined
                },
                {
                  key: 'permlink',
                  type: 'scalar',
                  offset: 20,
                  size: 12,
                  value: 'hello-world',
                  length: undefined,
                  children: undefined
                },
                {
                  key: 'weight',
                  type: 'scalar',
                  offset: 32,
                  size: 2,
                  value: '2200',
                  length: undefined,
                  children: undefined
                }
              ]
            }
          ]
        }
      ]
    },
    {
      key: 'extensions',
      type: 'array',
      offset: 34,
      size: 1,
      value: 'Length: 0',
      length: 0,
      children: []
    },
    {
      key: 'signatures',
      type: 'array',
      offset: 35,
      size: 1,
      value: 'Length: 0',
      length: 0,
      children: []
    }
  ]
}
```

===

+++ Python

TBA

+++

## Deserializing tranasction

This feature can be useful if you are reading transactions directly as a stream of bytes, previously serialized. We are already using transaction in binary form in plenty of Hive apps, such as: HAfAH, hived, etc.

+++ JavaScript

:::code source="../../../static/snippets/src/typescript/transaction/working-with-transaction/binary-view/from-binary.ts" language="typescript" title="Test it yourself: [src/typescript/transaction/working-with-transaction/binary-view/from-binary.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Ftransaction%2Fworking-with-transaction%2Fbinary-view%2Ffrom-binary.ts&startScript=test-transaction-working-with-transaction-binary-from)" :::

==- Output

```javascript
{
  ref_block_num: 22912,
  ref_block_prefix: 27667635,
  expiration: '2025-09-01T13:28:43',
  operations: [{
    type: 'vote_operation',
    value: [{
      voter: 'gtg',
      author: 'gtg',
      permlink: 'hello-world',
      weight: 2200
    }]
  }],
  extensions: [],
  signatures: []
}
```

===

+++ Python

TBA

+++
