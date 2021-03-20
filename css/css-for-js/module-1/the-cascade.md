# The cascade

If the browser has two conflicting rules, it needs to work out which one to apply

The browser works this out by looking at the specificity of the selector

- Classes are more specific than tags
- ids are more specific than classes

You can think of the cascade like the spread operator in js

```
const appliedStyles = {
  ...inheritedStyles,
  ...tagStyles,
  ...classStyles,
  ...idStyles,
  ...inlineStyles,
  ...importantStyles
}
```
