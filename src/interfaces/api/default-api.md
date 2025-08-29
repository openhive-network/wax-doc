---
order: -1
icon: database
label: JSON-RPC API
---

# Using default APIs

Wax provides an object-oriented interface for making and verifying API requests and responses. Hive API requests are arranged into various API categories:

- `account_by_key_api`: API requests related to reading account keys,
- `block_api`: API requests for fetching blockchain blocks,
- `database_api`: API requests for reading Hive state information,
- `network_broadcast_api`: API requests for broadcasting transactions to write to the blockchain,
- `rc_api`: API requests for reading/analyzing resource constraints (rc),
- etc.

## Regular Usage

The syntax for making an API call is:

```javascript
chainInstance.api[apiType][apiMethod](dataToSend);
```

### Fetching the first blockchain block

Using chain interface, you can retrieve a blockchain block. In the example below we use `block_api` as `apiType` and `get_block` as `apiMethod`:

+++ JavaScript

:::code source="../../static/snippets/src/typescript/api/default-api/retrieve-block.ts" language="typescript" title="Test it yourself: [src/typescript/api/default-api/retrieve-block.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fdefault-api%2Fretrieve-block.ts&startScript=test-api-default-api-retrieve-block)" :::

==- Output

```javascript
{
  block: {
    block_id: '0000000109833ce528d5bbfb3f6225b39ee10086',
    extensions: [],
    previous: '0000000000000000000000000000000000000000',
    signing_key: 'STM8GC13uCZbP44HzMLV6zPZGwVQ8Nt4Kji8PapsPiNq1BK153XTX',
    timestamp: '2016-03-24T16:05:00',
    transaction_ids: [],
    transaction_merkle_root: '0000000000000000000000000000000000000000',
    transactions: [],
    witness: 'initminer',
    witness_signature: '204f8ad56a8f5cf722a02b035a61b500aa59b9519b2c33c77a80c0a714680a5a5a7a340d909d19996613c5e4ae92146b9add8a7a663eef37d837ef881477313043'
  }
}
```

===

+++ Python

TBA

+++

### Changing Wax root's API server (endpointUrl)

Sometimes you may want to call `database_api` from a local API endpoint, while `get_block` from some of the [well-known API endpoint URLs](https://developers.hive.io/quickstart/#quickstart-hive-full-nodes). You can achieve it setting the endpointUrl property as in the example below:

+++ JavaScript

:::code source="../../static/snippets/src/typescript/api/default-api/set-endpoint.ts" language="typescript" title="Test it yourself: [src/typescript/api/default-api/set-endpoint.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fdefault-api%2Fset-endpoint.ts&startScript=test-api-default-api-set-endpoint)" :::

=== Output

```text
https://best.honey.provider
```

===

+++ Python

TBA

+++
