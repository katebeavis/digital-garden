# NodeList

A `NodeList` is a collection of `nodes`. It is an array like object that can be iterated over, using `forEach`. It can be converted into an array by using `Array.from()`

There are two types of `NodeList` = _live_ and _static_

## Live NodeList

In some cases a `NodeList` is _live_, meaning that when the DOM updates, the `NodeList` automatically updates

<!-- TODO add backlink -->

`Node.childNodes` is live

## Static NodeList

A _static_ `NodeList` does not update when the DOM updates

`querySelectorAll()` returns a static `NodeList`
