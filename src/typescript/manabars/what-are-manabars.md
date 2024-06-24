---
order: -1
icon: git-merge-queue
---

# Manabar types

## Understanding Hive's Manabars and Resource Credits

The Hive blockchain employs a unique system to manage user activities, particularly when it comes to voting, content creation, and resource utilization. This system leverages "manabars," a visual representation of available resources, to ensure fair and efficient usage. Here we delve into the different types of manabars, their functionalities, and the intricacies of Resource Credits (RC).

### Manabars on Hive Blockchain

Manabars on the Hive blockchain visually represent the remaining power for specific activities associated with an account. Let's explore the different types of manabars:

- **Voting Manabar**: This indicates the available voting power of an account. Each time a user votes, a portion of the voting power is utilized and gradually regenerates over time.
- **Downvote Manabar**: Similar to the voting manabar, this shows the power available for downvoting content. Downvotes consume a separate resource that also regenerates over time.
- **Resource Credits Manabar**: This bar represents the available Resource Credits (RC) which are critical for executing various transactions on the blockchain. Every transaction consumes a portion of RC, which regenerates over time based on the account's stake.

### How Manabars Work

1. **Resource Utilization**: Every activity on the Hive blockchain, whether it's posting content, voting, or making transactions, uses up a certain amount of resource from the corresponding manabar.
2. **Regeneration**: The power consumed by these activities is not lost forever. Manabars regenerate to full capacity over time, ensuring that active users can continue participating in the network.
3. **Proportional Limits**: The amount of resources an account can consume is directly proportional to the amount of Hive Power (vested stake) they have. Higher vested users have more resources and faster regeneration rates.

### Resource Credits Explained

**Resource Credits (RC)** are a form of bandwidth on the Hive blockchain, and they are essential for executing transactions. Here's what you need to know about RC:

- **Non-Transferable**: RCs are tied to individual Hive accounts and cannot be transferred or traded.
- **Regeneration**: Similar to the manabars, RCs regenerate over time. The rate of regeneration is proportional to the Hive Power of the account.
- **Transaction Cost**: Every transaction on the Hive blockchain consumes RCs. The more complex the transaction, the higher the RC cost.
- **Delegated RCs**: Accounts with more RCs than needed can delegate a portion to others.

### Examples

- **Voting**: When a user votes on a post, the voting manabar is depleted according to the vote weight. The depleted energy will start to regenerate over time.
- **Posting Content**: Creating a post or comment consumes RC proportional to the resource requirements, which include CPU cycles, state memory, and history size.
- **Account Creation**: Creating new accounts on Hive has a significant RC cost due to the resources it consumes.

### Visual Representation

Here's a typical view of a manabar on the Hive blockchain:

![Manabars visualization example on Hive Block Explorer](/static/manabars.webp)
