---
order: -4
icon: duplicate
expanded: false
label: Transaction and Operation
---

# Transaction and Operation Representation in the Hive Ecosystem

In the Hive ecosystem, transactions and operations are represented using specific data structures to ensure consistency and accuracy across applications. This standardized representation allows for seamless integration and interoperability among various services and tools within the ecosystem.

## Transactions

A **transaction** in the Hive ecosystem encapsulates all the operations that a user wants to execute. Each transaction contains metadata such as the expiration time and reference block information, along with the list of operations to be performed. Here is a general structure of a transaction:

- **ref_block_num**: A 16-bit integer referencing the block number.
- **ref_block_prefix**: A 32-bit integer referencing the block prefix.
- **expiration**: A timestamp indicating when the transaction expires.
- **operations**: A list of operations that are part of the transaction.
- **extensions**: Additional data or extensions provided in the transaction.

## Operations

**Operations** are the individual actions that can be contained within a transaction. Each operation corresponds to a specific action, such as transferring tokens, voting, or posting content.

Here's a general example of different operation types:

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

## Usage with Protobuf

Protobuf (Protocol Buffers) is a language-neutral and platform-neutral mechanism for serializing structured data. In the Hive ecosystem, Protobuf is used to define these transaction and operation data structures, making it easy to document and share these structures across different languages and platforms.

- **Protobuf Definitions**:
  - These definitions describe the data structures in a language-agnostic way.
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

This common definition provided by Protobuf allows for quick adaptation and ensures that different implementations (like those in the Wax library) are correctly aligned with the ecosystem's standards.