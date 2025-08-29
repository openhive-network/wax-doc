---
order: -1
icon: info
label: Implementation details
---


# Implementation details

> Chain interface (requires an endpoint) VS Base interface (no endpoint required)

This section is mainly for library maintainers who need to understand the low-level structure of the library.

## Root Interface Design Theory

The Base interface is a low-level interface that deals with basic functionalities that don't require communication with an API endpoint. About the only reason to directly use this interface is for creating an offline transaction signer, and even then the transactions first need to be constructed using an online application because valid hive transactions require current blockchain data. Here's a breakdown of what it includes:

1. **Transaction Building:**
   - Provides 3 methods for creating transactions. Each of them returns `ITransaction` type, the difference is only in parameters that each of those methods take:
      - `createTransactionFromProto` - taking a transaction in the proto form
      - `createTransactionFromJson` - taking a transaction in the Hive-API JSON form
      - `createTransactionWithTaPoS` - taking the taposBlockId and optionaly the expiration time.
   - Allows pushing operations into transactions, validating, signing, and building transactions.

2. **Asset Handling:**
   - Methods for handling HIVE, HBD, and VESTS in their native asset forms (`NaiAsset`).
   - Methods to convert these assets and calculate values, such as `hbdToHive`, `hive`, `hbd`, `vests`, and `vestsToHp`.

3. **Encryption and Decryption:**
   - Provides methods for encrypting and decrypting data using keys stored in a wallet.
   - Can securely suggest brain keys and derive private keys from passwords.

4. **Miscellaneous Utilities:**
   - Methods for working with manabar values, which relate to the user’s resource credits and voting power.
   - Conversion between different transaction and protocol formats.

## Hive Chain Interface

The Chain interface extends the functionalities of the Base interface and adds high-level network-related operations. This interface connects to a Hive API endpoint. Here are some highlights:

1. **Network Operations:**
   - **Creating transaction with Automatic Data Fetching:** It can fetch the head block or reference block data automatically, which is crucial for building and broadcasting transactions.
   - Provides high-level methods such as `createTransaction` which do not require the user to manually specify block IDs or other network data-related details.

2. **API Endpoint Management:**
   - Allows specifying and querying the API endpoint URL via `endpointUrl`.
   - Provides access to multiple pre-configured standard Hive RPC APIs (`account_by_key_api`, `block_api`, `database_api`, `network_broadcast_api`, `rc_api`).

3. **Extended API Capability:**
   - Supports extending the core API with custom APIs through the `extend` method, enabling custom RPC calls without losing the validation provided by the core API.

4. **Enhanced Manabar Calculation:**
   - Methods like `calculateCurrentManabarValueForAccount` and `calculateManabarFullRegenerationTimeForAccount` which fetch and calculate real-time blockchain account states directly from the network.
