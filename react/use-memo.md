# useMemo

## TLDR;

**useMemo - Allows you to cache a value between renders**

```
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

Returns a memoized value

Pass a create function and an array of dependencies. useMemo will only recompute the memoized value when one of the dependencies has changed. This optimization helps to avoid expensive calculations on every render

useMemo hook is very similar to useCallback, however, instead of returning an uncalled function as useCallback does, it calls the function being passed and only returns a result value when the array of parameters change. In other words, useMemo calls the passed function only when necessary and it returns a cached value on all the other renders

When a component is re-rendered, it creates new instances of all objects, including all the functions in it
