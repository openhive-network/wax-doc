---
order: -2
icon: sliders
expanded: false
label: Working with Transaction
---

# Working with Transaction

Basic purpose of `Transaction` interface is adding new operations to the (just created) transaction. Depending on complexity of given blockchain usage scenario, you can use a simple operation (directly correspondending to blockchain data type) or use dedicated complex operation class, which encapsulate complex details (at blockchain side) and simplify usage.
Beside of that active part, `Transaction` interface allows also to perform a data analysis on provided blockchain transaction: query for its digest (transaction id), acquire required authories like also list signatures specified for given transaction, to finally query for all public keys used to make given signatures.
