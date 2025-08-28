---
order: -1
icon: home
---

# Intro to Wax library

Wax is a multi-language, object-oriented library for interacting with the Hive blockchain network. There are currently three language implementations of the library: TypeScript, C++, and Python.  Each implementation of Wax incorporates the same code used by the core Hive protocol library to define Hive objects (operations, transactions, etc). This ensures that Wax will always maintain compatibility with the core blockchain protocol.

Wax enables developers to:

* read blockchain data from Hive API endpoints by making API requests
* write new blockchain data by creating and broadcasting Hive transactions containing various blockchain operations to Hive API endpoints

!!!secondary
This document contains executable examples that readers can directly interact with. When first opened, an example will automatically execute. You can also modify an example and re-run it. To re-run an example after modifying it, press the up-arrow in the terminal window to fetch the last command in the command line history (this is the command used to originally execute the example).
!!!

Start by exploring the Wax Interfaces reference:

[!ref icon="./static/typescript.svg" text="TypeScript Reference"](./typescript/config/init-general/)
