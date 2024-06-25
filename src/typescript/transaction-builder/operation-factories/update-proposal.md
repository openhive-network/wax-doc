---
order: -3
icon: tab-external
---

# Using UpdateProposal

The `UpdateProposalBuilder` allows for updating proposals on the Hive blockchain.

## Creating an Update Proposal

```typescript
import { createHiveChain, UpdateProposalBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const proposalId = 1;
const creator = "your-account";
const dailyPay = chain.hive(10000); // 100.000 HIVE
const subject = "Proposal Update";
const permlink = "proposal-update";

tx.useBuilder(UpdateProposalBuilder, () => {}, proposalId, creator, dailyPay, subject, permlink);

tx.build(); // builds the operation ready for broadcasting
```

## Adding an End Date to an Update Proposal

```typescript
import { createHiveChain, UpdateProposalBuilder } from '@hiveio/wax';

const chain = await createHiveChain();

const tx = new chain.TransactionBuilder('04c507a8c7fe5be96be64ce7c86855e1806cbde3', '2023-11-09T21:51:27');

const proposalId = 1;
const creator = "your-account";
const dailyPay = chain.hive(10000); // 100.000 HIVE
const subject = "Proposal Update";
const permlink = "proposal-update";
const endDate = '2023-03-14' // You can also give end date as a timestamp, eg. 1678917600000

tx.useBuilder(UpdateProposalBuilder, () => {}, proposalId, creator, dailyPay, subject, permlink, endDate);

tx.build(); // builds the operation ready for broadcasting
```
