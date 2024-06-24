---
order: -3
icon: rocket
---

# Using Custom Options

!!!secondary Optimization notice
Custom options allow configuring specific endpoints and settings to optimize for performance, network latency, or other custom needs.
!!!

## Initializing Wax interface with options

+++ Wax Base

```typescript
import { createWaxFoundation, IWaxOptions } from '@hiveio/wax';

// Define custom options
const customOptions: IWaxOptions = {
  chainId: 'f875a0b000000000000000000000000000000000000000000000000000000000' // Example custom chain ID
};

// Initialize Wax Foundation with custom options
await createWaxFoundation(customOptions);
```

+++ Wax Chain

```typescript
import { createHiveChain, IWaxOptionsChain } from '@hiveio/wax';

// Define custom options
const customOptions: IWaxOptionsChain = {
  chainId: 'f875a0b000000000000000000000000000000000000000000000000000000000', // Example custom chain ID
  apiEndpoint: 'https://hive.custom.endpoint' // Example custom API endpoint
};

// Initialize Hive Chain with custom options
createHiveChain(customOptions);
```

+++

These snippets demonstrate how to initialize the Wax Foundation and Hive Chain using either default or custom configuration options. By utilizing custom options, it's possible to optimize for specific performance or endpoint needs within the Hive ecosystem.
