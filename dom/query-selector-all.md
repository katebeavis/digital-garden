# querySelectorAll()

`querySelectorAll()` returns a (static) `NodeList` representing a list of the document's elements that match the specified group of selectors

e.g. to select all `p` elements present on a page:

```
const pElements = document.querySelectorAll('p');
```

This would return a `NodeList` of all `p` elements in the document

To find multiple elements, pass through a comma separated string:

```
const tabbableElements = document.querySelectorAll(
  'a[href], area[href], input:not([disabled]):not([type="hidden"]), select:not([disabled]), textarea:not([disabled]), button:not([disabled]), iframe, object, embed, [tabindex="0"], [contenteditable], audio[controls], video[controls], summary, [tabindex^="0"], [tabindex^="1"], [tabindex^="2"], [tabindex^="3"], [tabindex^="4"], [tabindex^="5"], [tabindex^="6"], [tabindex^="7"], [tabindex^="8"], [tabindex^="9"]'
);
```

This would return a `NodeList` of all tabbable elements
