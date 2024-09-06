---
order: -2
icon: sliders
expanded: false
label: Working with Transaction
---

# Working with Transaction

Basic purpose of `Transaction` interface is adding new operations to the (just created) transaction. Depending on complexity of given blockchain usage scenario, you can either use a simple operation (directly correspondending to blockchain data type) or use dedicated complex operation class that covers the complex details (at blockchain side) and simplifies usage.
In addition to this active part, the `Transaction` interface also allows you to perform a data analysis within the provided blockchain transaction: query its digest (transaction id), acquire required authorities like also list signatures specified for given transaction, and finally querying for all the public keys used to make given signatures.
