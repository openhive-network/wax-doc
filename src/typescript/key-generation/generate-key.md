---
order: -1
icon: passkey-fill
---

# Generate Private Key

In the context of the Hive ecosystem and specifically using the `@hiveio/wax` library, key generation can be achieved through two primary methods:

1. Derivation of a private key from a password (commonly referred to as a "Master Password" or "Brain Key").
2. Generation of a new private key (suggest brain key).

You can derive a private key from a password. This method is useful if you have a strong password and want to generate a private key for specific roles (active, owner, posting, memo) in your Hive account.

## Code Snippet to Generate a New Private Key or a Private Key from Password

```typescript
import { createWaxFoundation } from '@hiveio/wax';

const waxApi = await createWaxFoundation();
const accountName = "your-account";
const role = "active"; // roles can be 'active', 'owner', 'posting', or 'memo'
const masterPassword = "your-master-password";

// Generating a new private key from a password
const privateKeyData = waxApi.getPrivateKeyFromPassword(accountName, role, masterPassword);

console.log(`Associated Public Key: ${privateKeyData.associatedPublicKey}`);
console.log(`WIF Private Key: ${privateKeyData.wifPrivateKey}`);
```

!!!danger Security Reminder
**Always save the generated private keys and brain keys securely.** These keys provide access to your Hive account and assets. Importing them into Beekeeper ensures that you can use them securely for transactions and other operations without exposing the raw keys.
!!!
