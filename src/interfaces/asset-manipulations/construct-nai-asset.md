---
order: -1
icon: unread
---

# NaiAsset objects

There are three asset types (token types) in Hive's layer 1 protocol: HIVE (liquid hive), VESTS (staked hive), and HBD (hive-backed dollars). All asset amounts are specified as fixed-point numbers to prevent rounding errors (these are especially problematic for financial calculations) . Hive and HBD use 3 digits of precision, VESTS are specified using 6 digits of precision.

Assets can be represented using two formats. The first is the deprecated string format. Here's an example of the deprecated format for 1 Hive token: `"1.000 HIVE"`.

The second format is called Numeric Asset Identifier (NAI). NAI is the recommended format. With NAIs, asset types are specified using numbers rather than strings. NAIs were introduced to simplify supporting user-created asset types in the future.

Here's an example of an NAI asset for 1 hive token: `{"amount":"1000","precision":3,"nai":"@@000000021"}`.

!!!secondary Important note
NAI amounts must be specified as integer values (no decimal point) and the precision is used to shift the decimal place appropriately. The NAI field is used to specify the asset type: 21 is HIVE, 37 is VESTS, and 13 is HBD. Precision is fixed for each asset type (3 or 6), so when creating NAI objects, only the integer quantity and type must be specified.
!!!

## Creating NaiAsset objects for each asset type

+++ JavaScript

:::code source="../../static/snippets/src/typescript/asset-manipulations/construct-nai-asset/receive-nai-asset.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/receiving-nai-asset/receive-nai-asset.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Fconstruct-nai-asset%2Freceive-nai-asset.ts&startScript=test-asset-manipulations-receiving-nai-asset-receive-nai-asset)" :::

+++ Python

TBA

+++
