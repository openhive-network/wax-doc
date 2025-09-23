---
order: -2
icon: number
---

# Manabar calculations

Manabars in the Hive ecosystem represent the available resources for different activities such as upvoting, downvoting, and resource credits (RC). Each type of manabar regenerates over time and is pivotal in understanding an account's capacity to perform these activities.

## Common Parameters for Manabar Calculation for Wax Base interface

The calculations for each type of manabar follow a similar methodology, and they require some common parameters:

- `now`: Current head block time. (Timestamp in seconds)
- `maxMana`: Maximum account mana. Can be any numeric type, string or `BigInt`\*
- `currentMana`: Current account mana. Can be any numeric type, string or `BigInt`\*
- `lastUpdateTime`: Last update time of the current mana (in seconds)

> \* - (Only in **JavaScript** for large numbers)

## Calculation Methods using Wax Base Interface

### Upvote Manabar Calculation

To calculate the upvote manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxMana`: Equivalent to `post_voting_power.amount` from the `find_account` API call.
- `currentMana`: Equivalent to `voting_manabar.current_mana` from the `find_account` API call.
- `lastUpdateTime`: Equivalent to `voting_manabar.last_update_time` from the `find_account` API call

### Downvote Manabar Calculation

To calculate the downvote manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxMana`: Equivalent to `post_voting_power.amount` multiplied by `downvote_pool_percent` from the dynamic global properties.
- `currentMana`: Equivalent to `downvote_manabar.current_mana` from the `find_account` API call.
- `lastUpdateTime`: Equivalent to `downvote_manabar.current_mana` from the `find_account` API call.

### RC Manabar Calculation

To calculate the RC manabar, you need to gather the following values:

- `now`: Can be obtained using the `time` property from the dynamic global properties.
- `maxMana`: Equivalent to `max_rc` value from the `rc_accounts` API call.
- `currentMana`: Equivalent to `rc_manabar.current_mana` from the `rc_accounts` API call.
- `lastUpdateTime`: Equivalent to `rc_manabar.last_update_time` from the `rc_accounts` API call.

!!!secondary Blockchain state
Manabar calculations are sensitive to the latest blockchain state. Always fetch up-to-date dynamic global properties via API calls when using Wax Base interface. Wax Chain interface can automatically fetch required resources from the network using specified API endpoint.
!!!

## Example Usage

!!!light High level usage
You can also calculate the manabar values using high-level Wax Chain interface that automatically parses mentioned values from the chain and uses them for calculation for requested account.
!!!

### Calculation of Upvote Manabar for an Account

+++ JavaScript

:::code source="../../static/snippets/src/typescript/manabars/manabars-calculations/manabar-upvote-account.ts" language="typescript" title="Test it yourself: [src/typescript/manabars/manabars-calculations/manabar-upvote-account.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fmanabars%2Fmanabars-calculations%2Fmanabar-upvote-account.ts&startScript=test-manabars-manabars-calculations-manabar-upvote-account)" :::

+++ Python

:::code source="../../static/snippets/src/python/manabars/manabars_calculations/manabar_upvote_account.py" language="python" title="Test it yourself on github codespace: [src/python/manabars/manabars_calculations/manabar_upvote_account.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/manabars/manabars_calculations/manabar_upvote_account.py)" :::

+++

### Calculation of Full Regeneration Time for Downvote Manabar

+++ JavaScript

:::code source="../../static/snippets/src/typescript/manabars/manabars-calculations/manabar-downvote-account.ts" language="typescript" title="Test it yourself: [src/typescript/manabars/manabars-calculations/manabar-downvote-account.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fmanabars%2Fmanabars-calculations%2Fmanabar-downvote-account.ts&startScript=test-manabars-manabars-calculations-manabar-downvote-account)" :::

+++ Python

:::code source="../../static/snippets/src/python/manabars/manabars_calculations/manabar_downvote_account.py" language="python" title="Test it yourself on github codespace: [src/python/manabars/manabars_calculations/manabar_downvote_account.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/manabars/manabars_calculations/manabar_downvote_account.py)" :::

+++

### Calculation of Full Regeneration Time for Resource Credits Manabar

+++ JavaScript

:::code source="../../static/snippets/src/typescript/manabars/manabars-calculations/manabar-rc-account.ts" language="typescript" title="Test it yourself: [src/typescript/manabars/manabars-calculations/manabar-rc-account.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fmanabars%2Fmanabars-calculations%2Fmanabar-rc-account.ts&startScript=test-manabars-manabars-calculations-manabar-rc-account)" :::

!!!secondary Results parsing
Function `calculateManabarFullRegenerationTimeForAccount` returns a JavaScript `Date` object, which can be easily processed.

`calculateCurrentManabarValueForAccount` returns an object with manabar values and percent loaded.
!!!

+++ Python

:::code source="../../static/snippets/src/python/manabars/manabars_calculations/manabar_rc_account.py" language="python" title="Test it yourself on github codespace: [src/python/manabars/manabars_calculations/manabar_rc_account.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/manabars/manabars_calculations/manabar_rc_account.py)" :::

+++
