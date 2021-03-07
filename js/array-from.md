# Array.from

`Array.from` creates a shallow copy `Array` from an array like or iterable object

Takes the array like object as its first param and a map like fn as it's optional second param

```
const name = "kate"
Array.from(name) // ["k", "a", "t", "e"]

const numbers = [1, 2, 3, 4]
Array.from(numbers, x => x * 2) // [2, 4, 6, 8]
```

## From a NodeList

```
const images = document.getElementsByTagName('img');
const sources = Array.from(images, image => image.src);
const insecureSources = sources.filter(link => link.startsWith('http://'));
```
