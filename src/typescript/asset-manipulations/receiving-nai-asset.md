---
order: -1
icon: unread
---

# Receiving NaiAsset

Within the Hive ecosystem, asset conversions are a common requirement. The `@hiveio/wax` library facilitates these operations by providing methods to receive `NaiAsset` instances from given amounts.

Here’s how you can achieve this for different assets like HIVE, HBD, and VESTS.

## Code Snippet to Receive NaiAsset

:::code source="../../static/snippets/src/typescript/asset-manipulations/receiving-nai-asset/receive-nai-asset.ts" language="typescript" title="Test it yourself: [src/typescript/asset-manipulations/receiving-nai-asset/receive-nai-asset.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fasset-manipulations%2Freceiving-nai-asset%2Freceive-nai-asset.ts&startScript=test-asset-manipulations-receiving-nai-asset-receive-nai-asset)" :::

!!!warning Assets number representation
Make sure to provide the amount in integer form without decimal points. For example, `300.000 HIVE` should be represented as `300000` in the amount, not `300.0`.

Also remember that when dealing with assets in the Hive ecosystem, it's important to account for precision. The standard convention removes decimal points and adjusts the amount to an integer by factoring in precision. For example, if a token has 3 decimal places, `300.000 HIVE` should be represented as `300000` (3 decimal places removed). Always ensure you correctly handle asset precision in your implementation to avoid errors in calculations or representations.
!!!
