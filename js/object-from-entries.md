# Object.fromEntries

`Object.entries` transforms a list of key-value pairs into an object

```
const names = new Map([
  ["name", "kate"],
  ["name", "james"]
]);

Object.fromEntries(entries); // { name: "kate", name: "james" }
```

You can convert a Map or a nested array to an object

## Transforming an object

You can transform an object with the help from `Object.entries`

```
const object1 = { a: 1, b: 2, c: 3 };

Object.fromEntries(
  Object.entries(object1)
  .map(([ key, val ]) => [ key, val * 2 ])
); // { a: 2, b: 4, c: 6 }
```
