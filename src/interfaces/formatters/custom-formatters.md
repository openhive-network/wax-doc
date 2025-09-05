---
order: -4
icon: sort-asc
---

# Extending formatter

Operation formatters may be easily extended for formatting other operation types and Hive-related structures using `WaxFormattable` [TypeScript decorator](https://www.typescriptlang.org/docs/handbook/decorators.html).

`@WaxFormattable()` decorator specifies a custom formatter class method as a "formatter method" that matches objects with a given property name, by value or by instance of and transforms them. The property name can be specified in the decorator arguments as a string, as a property option or it defaults to the method name as the property name to match. By this, you can avoid problems like matching "get" or "constructor" properties.

Additionally, the new formatters are designed using [`reflect-metadata` library](https://www.npmjs.com/package/reflect-metadata), so if you have a method in the formatter class that does not have the mentioned decorator, then it will not be taken into account when formatting properties.

Options for the main formatter instance are passed to your custom formatter functions along the `source` and `target` objects, so you can also adapt your code to previously defined options.

!!!warning
**You should not modify `source` and `target` values passed to the formatter functions.** The target object will be formatted properly based on the formatter functions return value
!!!

Inside the formatter method specific to the given property, there will be passed an object as a first argument with readonly properties:

- `options` - Formatter options
- `source` - Source readonly unchanged input value for parsing raw data
- `target` - Target formatter data that might have been previously changed by other formatters

Upon leaving the function scope, you may return the value other than `undefined` if you want to change the matched property to the given data.

+++ Python

**Not implemented yet** — planned for a future release.

+++

## Regular Usage

### Matching property name by the function name

:::code source="../../static/snippets/src/typescript/formatters/custom-formatters/by-name.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/custom-formatters/by-name.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fcustom-formatters%2Fby-name.ts&startScript=test-formatters-custom-formatters-by-name)" :::

=== Output

```text
MyData: 12542
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++

### Matching property name and value for operation formatting

:::code source="../../static/snippets/src/typescript/formatters/custom-formatters/by-value.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/custom-formatters/by-value.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fcustom-formatters%2Fby-value.ts&startScript=test-formatters-custom-formatters-by-value)" :::

=== Output

```javascript
[
  'otom voted on @c0ff33a/ewxhnjbj',
  'oneplus7 transferred 300.000 HIVE to kryptogames'
]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++

### Matching property instance of for hive apps operation formatting

:::code source="../../static/snippets/src/typescript/formatters/custom-formatters/by-instance.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/custom-formatters/by-instance.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fcustom-formatters%2Fby-instance.ts&startScript=test-formatters-custom-formatters-by-instance)" :::

=== Output

```javascript
[ 'gtg delegated 0 to initminer' ]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++
