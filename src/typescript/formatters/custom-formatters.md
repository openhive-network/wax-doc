---
order: -4
icon: sort-asc
---

# Extending formatter

Operation formatters may be easily extended for formatting other operation types and Hive-related structures using `WaxFormattable` [TypeScript decorator](https://www.typescriptlang.org/docs/handbook/decorators.html).

## How it works

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

## Regular Usage

### Matching property name by the function name

```typescript
import { createHiveChain, WaxFormattable } from '@hiveio/wax';

const chain = await createHiveChain();

class MyFormatters {
  myFunction(value) {
    return value.toString();
  }

  @WaxFormattable()
  myCustomProp({ source }) {
    return this.myFunction(source.myCustomProp);
  }
}

const formatter = chain.formatter.extend(MyFormatters);

const data = {
  myCustomProp: 12542
};

console.log(formatter.waxify`MyData: ${data}`);
```

=== Output

```text
MyData: 12542
```

===

### Matching property name and value for operation formatting

```typescript
import { createHiveChain, WaxFormattable } from '@hiveio/wax';

const chain = await createHiveChain();

class OperationsFormatter {
  @WaxFormattable({ matchProperty: "type", matchValue: "transfer_operation" })
  public transferOperationFormatter({ source }): string {
    return `${source.value.from} transferred ${chain.waxify`${source.value.amount!}`} to ${source.value.to}`;
  }

  @WaxFormattable({ matchProperty: "type", matchValue: "vote_operation" })
  public voteOperationFormatter({ source }): string {
    return `${source.value.voter} voted on @${source.value.author}/${source.value.permlink}`;
  }
}

const formatter = chain.formatter.extend(OperationsFormatter);

const data = [{
  type: "vote_operation",
  value: {
    voter: "otom",
    author: "c0ff33a",
    permlink: "ewxhnjbj",
    weight: 2200
  }
}, {
  type: "transfer_operation",
  value: {
    from: "oneplus7",
    to: "kryptogames",
    amount: naiAsset,
    memo: "Roll under 50 4d434bd943616"
  }
}];

console.log(formatter.format(data));
```

=== Output

```javascript
[
  "otom voted on @c0ff33a/ewxhnjbj",
  "oneplus7 transferred 300.000 HIVE to kryptogames"
]
```

===

### Matching property instance of for hive apps operation formatting

```typescript
import { createHiveChain, WaxFormattable, ResourceCreditsOperation, ResourceCreditsOperationBuilder, IFormatFunctionArguments } from '@hiveio/wax';

const chain = await createHiveChain();

class HiveAppsOperationsFormatter {
  @WaxFormattable({ matchInstanceOf: ResourceCreditsOperation })
  public rcOperationFormatter({ target }: IFormatFunctionArguments<operation, { custom_json: ResourceCreditsOperation }>) {
    return `${target.custom_json.from} delegated ${target.custom_json.rc.amount} to ${target.custom_json.delegatees.join(",")}`;
  }
}

const tx = new chain.getTransactionBuilder();

tx.push(
  new ResourceCreditsOperationBuilder().removeDelegation("gtg", "initminer").authorize("gtg").build()
);

const formatter = chain.formatter.extend(HiveAppsOperationsFormatter);

console.log(formatter.format(tx.build().operations));
```

=== Output

```text
gtg delegated 0 to initminer
```

===
