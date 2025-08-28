---
order: -1
icon: comment-discussion
---

# Preface

Operation formatters provide a mechanism for converting complex operation objects into human-readable text representations.

## How Formatters Work

Formatters work by taking operation objects (such as transactions, custom JSON operations, NAI assets, witness properties etc.) and transforming them into strings or JavaScript objects based on predefined or custom formatting rules. The formatting rules can match specific properties or types within the operation objects and then apply the necessary transformations.

## Regular Usage

!!!secondary Object traverse direction
Wax transformers traverse given object from the bottom to the top without modifying the input data, e.g. in the following object, properties will be matched in the following order: 'a', 'b', 'c':

```json
{ b: { a: 10 }, c: 20 }
```

!!!
