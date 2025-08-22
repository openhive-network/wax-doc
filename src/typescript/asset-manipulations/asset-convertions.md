---
order: -3
icon: arrow-switch
---

# Asset Conversions
+++ TypeScript
Asset conversions are required for various Hive financial transactions. The `@hiveio/wax` library provides methods like `vestsToHp` and `hbdToHive` to facilitate these conversions.

## Using `vestsToHp`

The `vestsToHp` method converts VESTS into Hive Power (HP). This conversion requires three `NaiAsset` instances: one for the VESTS and two others for the total vesting fund Hive and total vesting shares.

### Code Snippet for `vestsToHp`

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fvests-to-hp.ts&startScript=test-asset-manipulations-asset-convertions-vests-to-hp)" :::

## Using `hbdToHive`

The `hbdToHive` method converts HBD into Hive. This conversion requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).

### Code Snippet for `hbdToHive`

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fhbd-to-hive.ts&startScript=test-asset-manipulations-asset-convertions-hbd-to-hive)" :::

+++ Python
Asset conversions are required for various Hive financial transactions. The `wax` library provides methods like `vests_to_hp` and `hbd_to_hive` to facilitate these conversions.

## Using `vests_to_hp`

The `vests_to_hp` method converts VESTS into Hive Power (HP). This conversion requires three `NaiAsset` instances: one for the VESTS and two others for the total vesting fund Hive and total vesting shares.

### Code Snippet for `vests_to_hp`

:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/vests_to_hp.py" language="python" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fvests-to-hp.ts&startScript=test-asset-manipulations-asset-convertions-vests-to-hp)" :::

## Using `hbd_to_hive`

The `hbd_to_hive` method converts HBD into Hive. This conversion requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).

### Code Snippet for `hbd_to_hive`

:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/hbd_to_hive.py" language="python" title="Test it yourself: [Try it on Codespace](https://github.com/codespaces/new/openhive-network/wax-doc-snippets?file=src/python/default_wax_initialization.py)" :::
