---
order: -2
icon: rocket
---

# Constructing a Wax interface

The root Wax interface can be constructed using either default or custom configuration options.
Custom options allow selecting a specific blockchain network (e.g. mainnet, testnet, or mirrornet), a specific Hive API endpoint (e.g. api.hive.blog) and also a custom REST API endpoint. It also provides settings to optimize for performance, network latency, or other custom needs.

## Default Wax initialization

+++ JavaScript

:::code source="../../static/snippets/src/typescript/config/init-general/chain.ts" language="typescript" title="Test it yourself: [src/typescript/config/init-general/chain.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fconfig%2Finit-general%2Fchain.ts&startScript=test-config-init-general-chain)" :::

+++

## Initializing Wax interface with custom options

+++ JavaScript

:::code source="../../static/snippets/src/typescript/config/init-general/chain-with-config.ts" language="typescript" title="Test it yourself: [src/typescript/config/init-general/chain-with-config.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fconfig%2Finit-general%2Fchain-with-config.ts&startScript=test-config-init-with-config-chain)" :::

+++
