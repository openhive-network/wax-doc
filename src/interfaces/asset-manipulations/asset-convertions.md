---
order: -3
icon: arrow-switch
---

# Asset Conversions

Asset conversions are required for various Hive financial transactions. The `@hiveio/wax` library provides methods like VESTS to HP and HBD to Hive to facilitate these conversions.

## VESTS to HP conversion

This method converts VESTS into Hive Power (HP). This conversion requires three `NaiAsset` instances: one for the VESTS and two others for the total vesting fund Hive and total vesting shares.

+++ JavaScript

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fvests-to-hp.ts&startScript=test-asset-manipulations-asset-convertions-vests-to-hp)" :::

+++ Python

TBA

+++

## HBD to HIVE conversion

This method converts HBD into Hive. This conversion requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).

You can retrieve the base and quote values from the [`database_api.get_current_price_feed`](https://developers.hive.io/apidefinitions/#database_api.get_current_price_feed) API call

+++ JavaScript

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fhbd-to-hive.ts&startScript=test-asset-manipulations-asset-convertions-hbd-to-hive)" :::

+++ Python

TBA

+++
