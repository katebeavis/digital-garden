# Arrays

## Destructuring

### Skip elements

```
const [cookie, , lolly] = ["🍪", "🍫", "🍭"];

console.log(cookie); // "🍪"
console.log(lolly); // "🍭"
```

### Assign a default value

```
const [cookie, chocolate, lolly, iceCream = "🍦"] = ["🍪", "🍫", "🍭"];
console.log(iceCream); // "🍦"
```

### Get all reminaing elements

```
const [cookie, ...remainingFood] = ["🍪", "🍫", "🍭"];
console.log(remainingFood); // ["🍫", "🍭"]]
```

### Unique

```
const food = ["🍪", "🍫", "🍫", "🍭", "🍪"];

// Create a new set from `food`, thereby removing all duplicates.
// Then, create a new array from it.
const uniqueFood = [...new Set(food)];

console.log(uniqueFood); // ["🍪", "🍫", "🍭"]
```

### Remove all falsy values from an array

```
const food = ["🍪", false, "🍫", undefined, "🍭"];

// Keep all array elements where `food` is truthy.
const filteredFood = food.filter(item => item);

console.log(filteredFood); // ["🍪", "🍫", "🍭"]
```

```
const filteredFood = food.filter(Boolean);
```

### Finding elements that are included in two arrays

```
const foodA = ["🍪", "🍫", "🍭"];
const foodB = ["🍭", "🍧", "🍦", "🍫"];

const intersection = foodA.filter(item => foodB.includes(item));
console.log(intersection); // ["🍫", "🍭"]
```

### Merge two arrays and remove duplicates

```
const foodA = ["🍪", "🍫", "🍭"];
const foodB = ["🍭", "🍧", "🍦", "🍫"];

// Merge `foodA` and `foodB`. Then, use a set for removing duplicates.
// After that, create a new array from the set.
const union = [...new Set([...foodA, ...foodB])];
console.log(union); // ["🍪", "🍫", "🍭", "🍧", "🍦"]
```

### Check if an array contains any element from another array

```
const foodA = ["🍪", "🍫", "🍭"];
const foodB = ["🍭", "🍧", "🍦", "🍫"];

const hasMatchingElements = foodA.some((item) => foodB.includes(item));
console.log(hasMatchingElements); // true
```

### Check if an array contains every element from another array

```
const foodA = ["🍪", "🍫", "🍭"];
const foodB = ["🍭", "🍧", "🍦", "🍫"];

const containsAllElements = foodA.every((item) => foodB.includes(item));
console.log(hasMatchingElements); // false

const foodA = ["🍪", "🍫", "🍭"];
const foodB = ["🍭", "🍪", "🍦", "🍫"];

const containsAllElements = foodA.every((item) => foodB.includes(item));
console.log(hasMatchingElements); // true
```
