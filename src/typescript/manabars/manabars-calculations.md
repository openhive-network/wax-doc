---
order: -2
icon: number
---

# Manabar calculations

Manabars in the Hive ecosystem represent the available resources for different activities such as upvoting, downvoting, and resource credits (RC). Each type of manabar regenerates over time and is pivotal in understanding an account's capacity to perform these activities.

## Common Parameters for Manabar Calculation for Wax Base interface

The calculations for each type of manabar follow a similar methodology, and they require some common parameters:

- `now`: Current head block time. (Timestamp in seconds)
- `maxManaLH`: Maximum account mana. Can be either `number`, `string` or [`long`](https://www.npmjs.com/package/long) (Used for large numbers)
- `currentManaLH`: Current account mana. Can be either `number`, `string` or [`long`](https://www.npmjs.com/package/long) (Used for large numbers)
- `lastUpdateTime`: Last update time of the current mana (in seconds)

## Calculation Methods using Wax Base Interface

### Upvote Manabar Calculation

To calculate the upvote manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxManaLH`: Equivalent to `post_voting_power.amount` from the `find_account` API call.
- `currentManaLH`: Equivalent to `voting_manabar.current_mana` from the `find_account` API call.
- `lastUpdateTime`: Equivalent to `voting_manabar.last_update_time` from the `find_account` API call

### Downvote Manabar Calculation

To calculate the downvote manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxManaLH`: Equivalent to `post_voting_power.amount` multiplied by `downvote_pool_percent` from the dynamic global properties.
- `currentManaLH`: Equivalent to `downvote_manabar.current_mana` from the `find_account` API call.
- `lastUpdateTime`: Equivalent to `downvote_manabar.current_mana` from the `find_account` API call.

### RC Manabar Calculation

To calculate the RC manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxManaLH`: Equivalent to `max_rc` value from the `rc_accounts` API call.
- `currentManaLH`: Equivalent to `rc_manabar.current_mana` from the `rc_accounts` API call.
- `lastUpdateTime`: Equivalent to `rc_manabar.last_update_time` from the `rc_accounts` API call.

!!!secondary Blockchain state
Manabar calculations are sensitive to the latest blockchain state. Always fetch up-to-date dynamic global properties via API calls when using Wax Base interface. Wax Chain interface can automatically fetch required resources from the network using specified API endpoint.
!!!

## Example Usage

!!!light High level usage
You can also calculate the manabar values using high-level Wax Chain interface that automatically parses mentioned values from the chain and uses them for calculation for requested account.
!!!

### Calculation of Upvote Manabar for an Account

```typescript
import { createHiveChain, EManabarType } from '@hiveio/wax';

const chain = await createHiveChain();
const fullRegenTime = await chain.calculateManabarFullRegenerationTimeForAccount("gtg", EManabarType.UPVOTE);
const manabarValue = await chain.calculateCurrentManabarValueForAccount("gtg", EManabarType.UPVOTE);

console.log("Full Regeneration Time for Upvote Manabar:", fullRegenTime, manabarValue.percent);
```

### Calculation of Full Regeneration Time for Downvote Manabar

```typescript
import { createHiveChain, EManabarType } from '@hiveio/wax';

const chain = await createHiveChain();
const fullRegenTime = await chain.calculateManabarFullRegenerationTimeForAccount("gtg", EManabarType.DOWNVOTE);
const manabarValue = await chain.calculateCurrentManabarValueForAccount("gtg", EManabarType.DOWNVOTE);

console.log("Full Regeneration Time for Downvote Manabar:", fullRegenTime, manabarValue.percent);
```

### Calculation of Full Regeneration Time for Resource Credits Manabar

```typescript
import { createHiveChain, EManabarType } from '@hiveio/wax';

const chain = await createHiveChain();
const fullRegenTime = await chain.calculateManabarFullRegenerationTimeForAccount("gtg", EManabarType.RC);
const manabarValue = await chain.calculateCurrentManabarValueForAccount("gtg", EManabarType.RC);

console.log("Full Regeneration Time for Resource Credits Manabar:", fullRegenTime, manabarValue.percent);
```

!!!secondary Results parsing
Function `calculateManabarFullRegenerationTimeForAccount` returns a JavaScript `Date` object, which can be easily processed.

`calculateCurrentManabarValueForAccount` returns an object with manabar values and percent loaded.
!!!
