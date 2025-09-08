---
order: 0
icon: rocket
---

# Getting Started

Wax enables developers to read and write data on the Hive blockchain. This guide will help you get started with the Wax library.

## Installing

First step is to install the library. Choose the appropriate installation command for your programming language.

+++ JavaScript

[!ref icon="../static/npm.svg" target="_blank" text="View **WAX** package on npmjs 🡭"](https://npmjs.com/package/@hiveio/wax)

```bash
pnpm add @hiveio/wax
```

> You can also use other package managers, such as: [`npm`](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm#using-a-node-version-manager-to-install-nodejs-and-npm) or [`yarn`](https://yarnpkg.com/getting-started/install)

+++ Python

TBA

+++

## Implementation details

**Base interface** (no endpoint required) VS **Chain interface** (requires an endpoint)

### Root Interface Design Theory

The Base interface is a low-level interface that deals with basic functionalities that don't require communication with an API endpoint. About the only reason to directly use this interface is for creating an offline transaction signer, and even then the transactions first need to be constructed using an online application because valid hive transactions require current blockchain data. Here's a breakdown of what it includes:

1. **Transaction Building:**
   - Provides 3 methods for creating transactions. Each of them returns `ITransaction` type, the difference is only in parameters that each of those methods take:
      - *Create transaction from Proto* - taking a transaction in the protobuf form
      - *Create transaction from JSON* - taking a transaction in the Hive-API JSON form
      - *Create transaction with TaPoS* - taking the taposBlockId and optionaly the expiration time.
   - Allows pushing operations into transactions, validating, signing, and building transactions.

2. **Asset Handling:**
   - Methods for handling *HIVE*, *HBD*, and *VESTS* in their native asset forms (*NAI*).
   - Methods to convert these assets and calculate values, such as *HBD to HIVE*, *HIVE to HBD*, *HIVE to VESTS*, and *VESTS to HP*.

3. **Encryption and Decryption:**
   - Provides methods for encrypting and decrypting data using keys stored in a wallet.
   - Can securely suggest brain keys and derive private keys from seeds.

4. **Miscellaneous Utilities:**
   - Methods for working with manabar values, which relate to the user's resource credits and voting power.
   - Conversion between different transaction and protocol formats.

### Hive Chain Interface

The Chain interface extends the functionalities of the Base interface and adds high-level network-related operations. This interface connects to a Hive API endpoint. Here are some highlights:

1. **Network Operations:**
   - Creating transaction with Automatic Data Fetching: It can fetch the head block or reference block data automatically, which is crucial for building and broadcasting transactions.
   - Provides high-level methods which do not require the user to manually specify block IDs or other network data-related details.

2. **API Endpoint Management:**
   - Allows specifying and querying the API with custom endpoint URL - global, per-API-category or per-request.
   - Provides access to multiple pre-configured standard Hive RPC APIs (`account_by_key_api`, `block_api`, `database_api`, `network_broadcast_api`, `rc_api`).

3. **Extended API Capability:**
   - Supports extending the core API with custom APIs through the *extend* and *extend REST* method, enabling custom RPC/REST calls with a full IntelliSense support.

4. **Enhanced Manabar Calculation:**
   - Multiple methods (including manabar-related calculations) which fetch and calculate real-time blockchain account states directly from the network.
