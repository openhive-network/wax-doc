---
order: -1
icon: database
---

# Using default APIs

`@hiveio/wax` provides a simple interface for calling and verifying API requests and responses (fully typed). Wax is delivered with a predefined set of APIs, like:

- `account_by_key_api`
- `block_api`
- `database_api`
- `network_broadcast_api`
- `rc_api`

## Regular Usage

!!!secondary
Wax uses [`class-validator`](https://www.npmjs.com/package/class-validator) and [`class-transformer`](https://www.npmjs.com/package/class-transformer) for requests and responses validation. It may throw if server responds with an unexpected value.
!!!

You can call API methods in the following favor:

```javascript
chainInstance.api[apiType][apiMethod](dataToSend);
```

### Retrieve specific block

Using Wax Formatters, you can format numbers represented as `string`, `number`, `BigInt` and [`long`](https://www.npmjs.com/package/long) using `formatNumber` method

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

const output = await chain.api.block_api.get_block({ block_num: 1 });

console.log(output);
```

==- Output

```javascript
GetBlockResponse {
  block: ApiBlock {
    extensions: [],
    transactions: [],
    transaction_ids: [],
    block_id: '0000000109833ce528d5bbfb3f6225b39ee10086',
    previous: '0000000000000000000000000000000000000000',
    signing_key: 'STM8GC13uCZbP44HzMLV6zPZGwVQ8Nt4Kji8PapsPiNq1BK153XTX',
    timestamp: '2016-03-24T16:05:00',
    transaction_merkle_root: '0000000000000000000000000000000000000000',
    witness: 'initminer',
    witness_signature: '204f8ad56a8f5cf722a02b035a61b500aa59b9519b2c33c77a80c0a714680a5a5a7a340d909d19996613c5e4ae92146b9add8a7a663eef37d837ef881477313043'
  }
}
```

===

### Specifying API endpoint URL for methods

Sometimes you may want to call `database_api` from a local Node, while `get_block` from some of the [well-known API endpoint URLs](https://developers.hive.io/quickstart/#quickstart-hive-full-nodes). You can achieve it using Wax feature: `setEndpointUrl`:

```typescript
import { createHiveChain } from '@hiveio/wax';

const chain = await createHiveChain();

chain.api.database_api.endpointUrl = "https://best.honey.provider"; // Custom endpoint URL for database_api

chain.endpointUrl = "https://api.hive.blog"; // This is default for all APIs

console.log(chain.api.database_api.endpointUrl);
```

=== Output

```text
https://best.honey.provider
```

===
