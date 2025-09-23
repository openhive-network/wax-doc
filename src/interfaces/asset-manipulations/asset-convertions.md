---
order: -3
icon: arrow-switch
---

# Asset Conversions

Asset conversions are required for various Hive financial transactions. The `@hiveio/wax` library provides methods like VESTS to HP and HBD to Hive to facilitate these conversions.

## VESTS to HP conversion

This method converts VESTS into Hive Power (HP). This conversion requires three `NaiAsset` instances or values convertible to `NaiAsset` (number, string or bigint for JavaScript): one for the VESTS and two others for the total vesting fund Hive and total vesting shares.

This method takes 3 parameters:

- *vests*: The amount of VESTS to convert.
- *total vesting fund*: The total amount of Hive in the vesting fund (Retrieved from the [`database_api.get_dynamic_global_properties`](https://developers.hive.io/apidefinitions/#database_api.get_dynamic_global_properties) API call - `total_vesting_fund_hive` property).
- *total vesting shares*: The total amount of vesting shares (Retrieved from the [`database_api.get_dynamic_global_properties`](https://developers.hive.io/apidefinitions/#database_api.get_dynamic_global_properties) API call - `total_vesting_shares` property).

+++ JavaScript

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fvests-to-hp.ts&startScript=test-asset-manipulations-asset-convertions-vests-to-hp)" :::

You can also perform the reverse conversion from HP to VESTS using the `hpToVests` method.

+++ Python

:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/vests_to_hp.py" language="python" title="Test it yourself on github codespace: [src/python/asset-manipulations/asset-conversion/vests_to_hp.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/asset-manipulations/asset-conversion/vests_to_hp.py)" :::

+++

## HBD to HIVE conversion

This method converts HBD into Hive. This conversion requires three `NaiAsset` instances or values convertible to `NaiAsset` (number, string or bigint for JavaScript): one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).

This method takes 3 parameters:

- *hbd*: The amount of HBD to convert.
- *base*: The base asset (Retrieved from the [`database_api.get_current_price_feed`](https://developers.hive.io/apidefinitions/#database_api.get_current_price_feed) API call - `base` property).
- *quote*: The quote asset (Retrieved from the [`database_api.get_current_price_feed`](https://developers.hive.io/apidefinitions/#database_api.get_current_price_feed) API call - `quote` property).

+++ JavaScript

:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fasset-convertions%2Fhbd-to-hive.ts&startScript=test-asset-manipulations-asset-convertions-hbd-to-hive)" :::

You can also perform the reverse conversion from HIVE to HBD using the `hiveToHbd` method.

+++ Python

:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/hbd_to_hive.py" language="python" title="Test it yourself on github codespace: [src/python/asset-manipulations/asset-conversion/hbd_to_hive.py](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/python/asset-manipulations/asset-conversion/hbd_to_hive.py)" :::

+++
