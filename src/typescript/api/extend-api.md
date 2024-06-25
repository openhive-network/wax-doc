---
order: -2
icon: cache
---

# Extending Chain

When writing an advanced Hive blockchain application in JavaScript, you may want to add more APIs to the standard set of Wax methods. There is a feature in Wax called `extend` allowing you to extend Wax Chain with fully-typed requests with or without validators.

## Regular Usage

!!!secondary
For these examples you will require [`class-validator`](https://www.npmjs.com/package/class-validator) package for requests and responses validation.
!!!

### Virtually extend chain

If you do not want to implement your own validators, there is a simple interface to do so:

```typescript
import { createHiveChain, TWaxApiRequest, TWaxExtended } from '@hiveio/wax';

const chain = await createHiveChain();

// https://developers.hive.io/apidefinitions/#transaction_status_api.find_transaction-parameter_json
// Create a request interface without validators - this will be the input from the end user
interface IFindTransactionRequest {
  transaction_id: string;
  expiration: string;
}

// https://developers.hive.io/apidefinitions/#transaction_status_api.find_transaction-expected_response_json
// Create a response interface without validators - this will be the output from the remote API
interface IFindTransactionResponse {
  status: 'unknown' | string;
}

// Create the proper API structure
type TExtendedApi = {
  transaction_status_api: { // API
    find_transaction: TWaxApiRequest<IFindTransactionRequest, IFindTransactionResponse> // Method
  }
};

const extended = chain.extend<TExtendedApi>();

// Call the transaction_status_api API using our extended interface
const result = await extended.api.transaction_status_api.find_transaction({
  transaction_id: "0000000000000000000000000000000000000000",
  expiration: "2016-03-24T18:00:21"
});

console.info(result);
```

=== Output

```javascript
{ status: 'unknown' }
```

===

As you see in the example, there is a type called: `TWaxApiRequest` which as a first template argument takes a user input type (that the user will have to pass to the API request function). It may be an `interface`, but it can also be a standard type, like: `boolean`, `number`, `Array` and so on. The second argument should be the response type (type of `result` in the snippet above).

### Extending Chain with validators

In order to create validators, you have to create a separate class for: request and response and create a proper API structure, like in the example (for `transaction_status_api.find_transaction`):

```typescript
import { IsHexadecimal, IsDateString, IsString } from 'class-validator';
import { createHiveChain, TWaxExtended } from '@hiveio/wax';

const chain = await createHiveChain();

// https://developers.hive.io/apidefinitions/#transaction_status_api.find_transaction-parameter_json
// Create a request class with validators that will require a valid input from the end user
class FindTransactionRequest {
  @IsHexadecimal()
  public transaction_id!: string;

  @IsDateString()
  public expiration!: string;
}

// https://developers.hive.io/apidefinitions/#transaction_status_api.find_transaction-expected_response_json
// Create a response class with validators that will require a valid output from the remote API
class FindTransactionResponse {
  @IsString()
  public status!: 'unknown' | string;
}

// Create the proper API structure
const ExtendedApi = {
  transaction_status_api: { // API
    find_transaction: { // Method
      params: FindTransactionRequest, // params is our request
      result: FindTransactionResponse // result is out response
    }
  }
};

const extended: TWaxExtended<typeof ExtendedApi> = chain.extend(ExtendedApi);

// Call the transaction_status_api API using our extended interface
const result = await extended.api.transaction_status_api.find_transaction({
  transaction_id: "0000000000000000000000000000000000000000",
  expiration: "2016-03-24T18:00:21"
});

console.info(result);

```

=== Output

```javascript
{ status: 'unknown' }
```

===
