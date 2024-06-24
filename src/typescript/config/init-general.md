---
order: -2
icon: rocket
---

# General wax initialization

**Note:** Using default options provides ease-of-use and simplicity but might not be optimized for specific performance needs or endpoints.

## Initializing Wax interface

+++ Wax Base

```typescript
import { createWaxFoundation } from '@hiveio/wax';

// Initialize Wax Foundation using default options
await createWaxFoundation();
```

+++ Wax Chain

```typescript
import { createHiveChain } from '@hiveio/wax';

// Initialize Hive Chain using default options
await createHiveChain();
```

+++
