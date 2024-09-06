---
order: -2
icon: sliders
expanded: false
label: Working with Transaction
---

# Working with Transaction

Basic purpose of `Transaction` interface is adding new operations to the modified transaction. Depending on complexity of given blockchain operation, you can make it directly or use dedicated operation class, hiding complex details and simplifying usage.
Beside of that, `Transaction` interface allows also to retrieve several complex data from transaction. It is initialized with: query for its digest (transaction id), list signatures specified/added to given transaction and finally query for all public keys used to make given signatures.
