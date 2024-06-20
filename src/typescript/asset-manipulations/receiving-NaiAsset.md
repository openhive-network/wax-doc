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

### Important Note
Make sure to provide the amount in integer form without decimal points. For example, `300.000 HIVE` should be represented as `300000` in the amount, not `300.0`.
