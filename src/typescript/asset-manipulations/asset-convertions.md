---
order: -2
icon: arrow-switch
---

# Asset Conversions

Asset conversions in the Hive ecosystem are crucial for various financial transactions. The `@hiveio/wax` library provides methods like `vestsToHp` and `hbdToHive` to facilitate these conversions.

## Using `vestsToHp`

The `vestsToHp` method converts VESTS into Hive Power (HP). This conversion requires three `NaiAsset` instances: one for the VESTS and two others for the total vesting fund Hive and total vesting shares.

### Code Snippet for `vestsToHp`
```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Create a Wax Foundation instance
const waxApi = await createWaxFoundation();

// Assume these amounts represent the vests, totalVestingFundHive, and totalVestingShares
const vestsAmount = 10000;
const totalVestingFundHiveAmount = 20000;
const totalVestingSharesAmount = 50000;

// Convert amounts to `NaiAsset`
const vestsAsset = waxApi.vests(vestsAmount);
const totalVestingFundHiveAsset = waxApi.hive(totalVestingFundHiveAmount);
const totalVestingSharesAsset = waxApi.vests(totalVestingSharesAmount);

// Use `vestsToHp` to perform the conversion
const hpAsset = waxApi.vestsToHp(vestsAsset, totalVestingFundHiveAsset, totalVestingSharesAsset);
console.log(`HP Asset: ${JSON.stringify(hpAsset)}`);
```

## Using `hbdToHive`

The `hbdToHive` method converts HBD into Hive. This conversion requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).

### Code Snippet for `hbdToHive`
```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Create a Wax Foundation instance
const waxApi = await createWaxFoundation();

// Assume these amounts represent the HBD, base, and quote
const hbdAmount = 1000;
const baseAmount = 1500;
const quoteAmount = 2000;

// Convert amounts to `NaiAsset`
const hbdAsset = waxApi.hbd(hbdAmount);
const baseAsset = waxApi.hbd(baseAmount);
const quoteAsset = waxApi.hive(quoteAmount);

// Use `hbdToHive` to perform the conversion
const hiveAsset = waxApi.hbdToHive(hbdAsset, baseAsset, quoteAsset);
console.log(`Converted Hive Asset: ${JSON.stringify(hiveAsset)}`);
```
