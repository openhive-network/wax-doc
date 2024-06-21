---
order: -2
icon: sliders
expanded: false
label: Working with TB
---

# Working with Transaction Builder

Basic purpose of `TransactionBuilder` tool is adding new operations to the modified transaction. Depending on complexity of given blockchain operation, you can make it directly or use dedicated operation builder class, hiding complex details and simplifying usage.
Beside of that, `TransactionBuilder` allows also to retrieve several complex data from transaction it is initialized with: query for its digest (transaction id), list signatures specified/added to given transaction and finally query for all public keys used to make given signatures.
