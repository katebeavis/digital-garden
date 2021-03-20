# Selectors

CSS comes with an incredibly rich set of selectors, and those selectors can be mixed and matched in interesting ways

## Pseudo-classes

A pseudo-class is a selector modifier - it will apply its declarations when some sort of condition or state is met

```
button:hover {
  color: blue;
}
```

### Focus

In HTML, there is always an 'active' element

- This is the element that is currently selected
- When a button is clicked, focus moves to that button
- By default, the body tag is focused. When focus moves to an interactive element, that element gets an outline link

### Checked

`:checked` only applies to checkboxes and radio buttons that are 'filled in'

## Descendant selectors

The descendant selector consists of a space-separated set of selectors and matches all descendants, regardless of how deep they are nested

The below will target all `<a>` within the `<nav>`

```
nav a {
  color: red;
}
```

You can select the direct child by using the more than selector `>`

The below would only select the `<a>` that are direct descendants of `<nav>`

```
nav > a {
  color: red;
}
```
