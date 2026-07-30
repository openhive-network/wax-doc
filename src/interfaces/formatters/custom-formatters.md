---
order: -4
icon: sort-asc
---

# Extending formatter

+++ JavaScript

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

+++ Rust

Operation formatters may be easily extended for formatting other operation types and Hive-related structures using the `#[hive_formatter]` attribute macro — the Rust analog of a TypeScript custom formatter class with `@WaxFormattable` methods.

`#[hive_formatter]` is applied to an inherent `impl` block and generates a `CustomFormatter` implementation from it, ready to be registered with `formatter.extend::<MyFormatters>()` (which derives a new formatter — the one it is called on is never mutated). Every method marked with the `#[format]` attribute becomes a "formatter method" of the shape:

```rust
#[format]
fn property_name(&self, ctx: &FormatContext<'_>, source: T) -> Option<R>
```

The matched property defaults to the method name; use `#[format(rename = "camelCaseProp")]` when a snake_case method name cannot spell the property, or match another property — optionally with a specific value — using `#[format(match_property = "type", match_value = "transfer_operation")]` (`require_defined` additionally skips nodes whose property value is `null`). Methods without the `#[format]` attribute are not taken into account when formatting properties.

The `source` parameter is the matched node deserialized into the method's typed parameter (`serde_json::Value` accepts any shape; a failed deserialization skips the rule), and `R` serializes into the replacement. Returning `Some(value)` replaces the matched property with the given data; returning `None` leaves the node unchanged.

The `FormatContext` passed as the first argument carries readonly references:

- `options` - Formatter options
- `source` - Source readonly unchanged input value for parsing raw data
- `target` - Target formatter data that might have been previously changed by other formatters

!!!secondary
Unlike in TypeScript, input immutability is enforced by the compiler: `source` and `target` are shared references, and the target tree is rebuilt from the formatter methods' return values.
!!!

If the impl block defines a `fn new(wax: FoundationHandle) -> Self`, the generated `CustomFormatter::create` calls it with the shared foundation handle (the analog of the optional TS custom formatter constructor); otherwise it falls back to `Default::default()`.

+++

## Regular Usage

### Matching property name by the function name

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/custom-formatters/by-name.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/custom-formatters/by-name.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fcustom-formatters%2Fby-name.ts&startScript=test-formatters-custom-formatters-by-name)" :::

=== Output

```text
MyData: 12542
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

:::code source="../../static/snippets/src/rust/formatters/custom_formatters/by_name.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/custom_formatters/by_name.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/custom_formatters/by_name.rs)" :::

=== Output

```text
MyData: 12542
```

===

+++

### Matching property name and value for operation formatting

+++ JavaScript

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

+++ Rust

:::code source="../../static/snippets/src/rust/formatters/custom_formatters/by_value.rs" language="rust" title="Test it yourself on github codespace: [src/rust/formatters/custom_formatters/by_value.rs](https://github.com/codespaces/new?repo=openhive-network/wax-doc-snippets&ref=main&file=workspaces/wax-doc-snippets/src/rust/formatters/custom_formatters/by_value.rs)" :::

=== Output

```json
[
  "otom voted on @c0ff33a/ewxhnjbj",
  "oneplus7 transferred 300.000 HIVE to kryptogames"
]
```

===

+++

### Matching property instance of for hive apps operation formatting

+++ JavaScript

:::code source="../../static/snippets/src/typescript/formatters/custom-formatters/by-instance.ts" language="typescript" title="Test it yourself: [src/typescript/formatters/custom-formatters/by-instance.ts](https://stackblitz.com/github/openhive-network/wax-doc-snippets?file=src%2Ftypescript%2Fformatters%2Fcustom-formatters%2Fby-instance.ts&startScript=test-formatters-custom-formatters-by-instance)" :::

=== Output

```javascript
[ 'gtg delegated 0 to initminer' ]
```

===

+++ Python

**Not implemented yet** — planned for a future release.

+++ Rust

!!!secondary No `matchInstanceOf` in Rust
`matchInstanceOf` matching is not available: the formatter serializes its input through serde before traversal, so no runtime type identity survives in the resulting JSON tree — rules can only match nodes by property name and value. The closest counterpart is `FormatterRegistry::register_instance`, which matches the concrete Rust type of the value passed directly to `format` (the typed root), before serialization.
!!!

+++
