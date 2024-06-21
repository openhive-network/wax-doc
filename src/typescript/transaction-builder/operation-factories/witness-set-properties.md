---
order: -4
icon: people
---

# Setting Witness Properties

The `WitnessSetPropertiesBuilder` allows witnesses to update their properties on the Hive blockchain.

## Setting Default Witness Properties

```typescript
import { createHiveChain, WitnessSetPropertiesBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const owner = 'witness-account';
const key = 'STM8...' // Public key

tx.useBuilder(WitnessSetPropertiesBuilder, () => {}, owner, key);

tx.build(); // builds the operation ready for broadcasting
```

## Setting Explicit Witness Properties

Just like in comment builder, you can use multiple values on one builder instance.

```typescript
import { createHiveChain, WitnessSetPropertiesBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const owner = "witness-account";
const witnessKey = "STM8..."; // Public key
const maxBlockSize = 65536;
const hbdInterestRate = 750; // 7.5%
const accountCreationFee = chain.hive(30000); // 300.000 HIVE
const witnessUrl = "https://witness.example.com";

tx.useBuilder(WitnessSetPropertiesBuilder, builder => {
    builder
        .setMaximumBlockSize(maxBlockSize)
        .setHBDInterestRate(hbdInterestRate)
        .setAccountCreationFee(accountCreationFee)
        .setUrl(witnessUrl);
}, owner, key);

tx.build(); // builds the operation ready for broadcasting
```
