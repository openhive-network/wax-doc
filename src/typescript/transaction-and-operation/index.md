---
order: -3
icon: duplicate
expanded: false
label: Blockchain data types
---

# Hive Protocol: Transaction and Operations

Hive transactions, operations and their properties (i.e. assets) are represented using specific types and data structures defined inside the Hive Protocol library. These objects are initially defined using Protobuf, and language-specific versions are generated from the Protobuf code. This standardized representation allows for seamless integration and interoperability among various services and tools within the ecosystem.

## Transactions

Hive **transactions** are created by a user to group a sequence of Hive operations that should all succeed or fail together.  Even singular operations need to be put inside a transaction because account signing is also performed at the transaction level. In addition to a sequence of operations, each transaction contains metadata such as the expiration time. 

FULL EXPLANATIONS NEED TO BE ADDED HERE ABOUT TAPOS AND EXPIRATION TIME AFTER MORE RESEARCH.

Here is a general structure of a transaction:

- **ref_block_num**: A 16-bit integer referencing the block number.
- **ref_block_prefix**: A 32-bit integer referencing the block prefix.
- **expiration**: A timestamp indicating when the transaction expires.
- **operations**: A list of operations that are part of the transaction.
- **extensions**: Additional data or extensions provided in the transaction.
- **signatures**: A list of cryptographic signatures generated for given transaction. Can be empty for unsigned transactions.

## Operations

**Operations** are commands to the blockchain processing engine. Example operations include transferring tokens, adding text posts to the blockchain, voting for posts, voting for witnesses, etc.

Here are some examples of the contents of some operations:

- **transfer_operation**: Handles token transfers between accounts.
  - **from**: The sender's account name.
  - **to**: The receiver's account name.
  - **amount**: The amount to be transferred.
  - **memo**: An optional memo for the transfer.

- **vote_operation**: Handles voting on content.
  - **voter**: The account name of the voter.
  - **author**: The account name of the post author.
  - **permlink**: The permanent link to the content.
  - **weight**: The weight of the vote.

- **comment_operation**: Handles posting or editing content.
  - **parent_author**: The account name of the parent post author (for comments).
  - **parent_permlink**: The permanent link to the parent content.
  - **author**: The account name of the author.
  - **permlink**: The permanent link to the content.
  - **title**: The title of the post.
  - **body**: The content body.
  - **json_metadata**: Additional metadata in JSON format.

YOU CAN FIND A FULL LIST OF POSSIBLE OF OPERATIONS AND THEIR FIELDS HERE. ADD LINK TO PROTOBUF GENERATED DOCUMENTATION HERE.

WHY IS THERE A MISMATCH BETWEEN NAMES IN EXAMPLES ABOVE AND PROTOBUF DEFINITIONS?

## Implementation Note: Why use Protobuf?

Protobuf (Protocol Buffers) is a language-neutral and platform-neutral mechanism for serializing structured data. Hive uses Protobuf definitions for transaction and operation data structures in order to make it easy to document and share these structures across different languages and platforms. These common definitions enable safe and rapid update to the Hive protocol while ensuring that different implementations (like those in the Wax library) are correctly aligned with the blockchain network's protocol standard.

- **Protobuf Definitions**:
  - These definitions describe the data structures in a language-agnostic way.
  - They are defined directly inside the Hive Protocol library and shared from there
  - Examples:
    ```protobuf
    message transfer {
      required string from_account = 1 [json_name = "from"];
      required string to_account = 2 [json_name = "to"];
      required asset  amount = 3;
      required string memo = 4;
    }

    message vote {
        required string voter = 10;
        required string author = 11;
        required string permlink = 12;
        required uint32 weight = 13;
    }

    message comment {
        required string parent_author = 1 [json_name = "parent_author"];
        required string parent_permlink = 2 [json_name = "parent_permlink"];
        required string author = 3;
        required string permlink = 4;
        required string title = 5;
        required string body = 6;
        required string json_metadata = 7 [json_name = "json_metadata"];
    }
    ```
