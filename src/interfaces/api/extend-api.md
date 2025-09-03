---
order: -2
icon: cache
label: Custom API endpoints
---

# Extending Chain

When writing an advanced Hive blockchain application, you may want to add more APIs to the standard set of Wax methods. There is a feature in Wax called `extend` or `extendRest` (for REST API) allowing you to extend Wax Chain with fully-typed requests with full typization.

![Wax extended using HAfAH REST API package - Full IntelliSense support](../../static/intellisense-rest-api.png)

## Add simple endpoint

+++ JavaScript

:::code source="../../static/snippets/src/typescript/api/extend-api/interface-extend.ts" language="typescript" title="Test it yourself: [src/typescript/api/extend-api/interface-extend.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fextend-api%2Finterface-extend.ts&startScript=test-api-extend-api-interface-extend)" :::

=== Output

```javascript
{ "is_known": false }
```

===

As you can see in the example, there is a type called: `TWaxApiRequest` which as a first template argument takes a user input type (that the user will have to pass to the API request function). It may be an `interface`, but it can also be a standard type, like: `boolean`, `number`, `Array` and so on. The second argument should be the response type (type of `result` in the snippet above).

+++ Python

TBA

+++

## Manually extending REST API

+++ JavaScript

:::code source="../../static/snippets/src/typescript/api/extend-api/interface-extend-rest.ts" language="typescript" title="Test it yourself: [src/typescript/api/extend-api/interface-extend-rest.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fextend-api%2Finterface-extend-rest.ts&startScript=test-api-extend-api-interface-extend-rest)" :::

=== Output

```javascript
{
  previous: '00bc614d58b1745f3347e4f55f35fe68c82ad0d1',
  timestamp: '2017-05-29T06:28:42',
  witness: 'good-karma',
  transaction_merkle_root: '3843fd6daebf3742ecc84fe5926df037131a66a6',
  extensions: []
}
```

===

+++ Python

TBA

+++

## Automatically extending REST API

As you can see it is a little complicated and REST API can potentially change frequently as it is not consensus-based, so we created multiple packages, automatically generating API definitions from OpenAPI definitions for each endpoint. You would only need to install the package and use the generated types:

+++ JavaScript

[!ref icon="../../static/npm.svg" target="_blank" text="View **HAfAH** API package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-api-hafah)
[!ref icon="../../static/npm.svg" target="_blank" text="View **Block Explorer** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-api-hafbe)
[!ref icon="../../static/npm.svg" target="_blank" text="View **Reputation Tracker** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-api-reputation-tracker)
[!ref icon="../../static/npm.svg" target="_blank" text="View **Balance Tracker** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax-api-balance-tracker)

Example usage:

```javascript
import HAfAH from "@hiveio/wax-api-hafah";

const extendedChain = chain.extendRest(HAfAH);
// You can now call extendedChain.restApi...<methodNames>()
```

+++ Python

TBA

+++
