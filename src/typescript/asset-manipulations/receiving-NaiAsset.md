---
order: -1
icon: unread
---

# Receiving NaiAsset

Within the Hive ecosystem, asset conversions are a common requirement. The `@hiveio/wax` library facilitates these operations by providing methods to receive `NaiAsset` instances from given amounts.

Here’s how you can achieve this for different assets like HIVE, HBD, and VESTS.

## Code Snippet to Receive NaiAsset

```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Create a Wax Foundation instance
const waxApi = await createWaxFoundation();

// Assume the existence of some amount
const amount = 1000;

// Convert the amount into `NaiAsset` for HIVE, HBD, and VESTS
const hiveAsset = waxApi.hive(amount);
const hbdAsset = waxApi.hbd(amount);
const vestsAsset = waxApi.vests(amount);

console.log(`Hive Asset: ${JSON.stringify(hiveAsset)}`);
console.log(`HBD Asset: ${JSON.stringify(hbdAsset)}`);
console.log(`Vests Asset: ${JSON.stringify(vestsAsset)}`);
```

!!!warning Assets number representation
Make sure to provide the amount in integer form without decimal points. For example, `300.000 HIVE` should be represented as `300000` in the amount, not `300.0`.

Also remember that when dealing with assets in the Hive ecosystem, it's important to account for precision. The standard convention removes decimal points and adjusts the amount to an integer by factoring in precision. For example, if a token has 3 decimal places, `300.000 HIVE` should be represented as `300000` (3 decimal places removed). Always ensure you correctly handle asset precision in your implementation to avoid errors in calculations or representations.
!!!
