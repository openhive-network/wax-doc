---
order: -2
icon: cache
---

# Extending Chain

When writing an advanced Hive blockchain application in JavaScript, you may want to add more APIs to the standard set of Wax methods. There is a feature in Wax called `extend` allowing you to extend Wax Chain with fully-typed requests (with or without validators).

## Regular Usage

!!!secondary
For these examples, you will require [`class-validator`](https://www.npmjs.com/package/class-validator) package for requests and responses validation.
!!!

### Virtually extend chain

If you do not want to implement your own validators, here is a simple interface to do so:

:::code source="../../static/snippets/src/typescript/api/extend-api/interface-extend.ts" language="typescript" title="Test it yourself: [src/typescript/api/extend-api/interface-extend.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fextend-api%2Finterface-extend.ts&startScript=test-api-extend-api-interface-extend)" :::

=== Output

```javascript
{ status: 'too_old' }
```

===

As you can see in the example, there is a type called: `TWaxApiRequest` which as a first template argument takes a user input type (that the user will have to pass to the API request function). It may be an `interface`, but it can also be a standard type, like: `boolean`, `number`, `Array` and so on. The second argument should be the response type (type of `result` in the snippet above).

### Extending Chain with validators

In order to create validators, you have to create a separate class for: request and response and create a proper API structure, like in the example (for `transaction_status_api.find_transaction`):

:::code source="../../static/snippets/src/typescript/api/extend-api/validate-extend.ts" language="typescript" title="Test it yourself: [src/typescript/api/extend-api/validate-extend.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fapi%2Fextend-api%2Fvalidate-extend.ts&startScript=test-api-extend-api-validate-extend)" :::

=== Output

```javascript
FindTransactionResponse { status: 'too_old' }
```

===
