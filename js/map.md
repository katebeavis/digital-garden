# Map

Map is a collection of keyed data items, just like an Object. But the main difference is that Map allows keys of any type

Map was introduced in es6 as using objects as a map has some side effects:

- An object always has a default key like the prototype
- A key of an object must be a string or a symbol, you cannot use an object as a key
- An object does not have a property that represents the size of the map

By definition, a Map object holds key-value pairs where values of any type can be used as either keys or values. In addition, a Map object remembers the original insertion order of the keys

`const map = new Map()`

- `clear()` – removes all elements from the map object.
- `delete(key)` – removes an element specified by the key. It returns if the element is in the map, or false if it does not.
- `entries()` – returns a new Iterator object that contains an array of [key, value] for each element in the map object. The order of objects in the map is the same as the insertion order.
- `forEach(callback[, thisArg])` – invokes a callback for each key-value pair in the map in the insertion order. The optional thisArg parameter sets the this value for each callback.
- `get(key)` – returns the value associated with the key. If the key does not exist, it returns undefined.
- `has(key)` – returns true if a value associated with the key exists, otherwise, return false.
- `keys()` – returns a new Iterator that contains the keys for elements in insertion order.
- `set(key, value)` – sets the value for the key in the map object. It returns the map object itself therefore you can chain this method with other methods.
- `values()` returns a new iterator object that contains values for each element in insertion order.

```
const users = new Map([['dave', '28'],['bob', '42']])
// iterate over keys
for (let name of users.keys()) {
  alert(name); // dave, bob
}

// iterate over values
for (let age of users.values()) {
  alert(age); // 28, 52
}

// iterate over [key, value] entries
for (let entry of users) { // the same as of users.entries()
  alert(entry); // dave,28 (and so on)
}
```
