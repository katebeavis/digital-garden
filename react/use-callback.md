# useCallback

## TLDR;

**useCallback - Allows you to cache an instance of a function between renders**

```
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```

Returns a memoized callback

Pass an inline callback and array of dependencies. useCallback will return a memoized version of the callback that only changes if one of the dependencies has changed. This helps to reduce expensive calculations on every render

Useful when you have a component with a child frequently re-rendering, and you pass a callback to it

Each re-render, the Child will re-execute its function prop uselessly. If you pass useCallback as a prop with a dependency array, it resolves the issue because the function will be executed only when the dependency changes. Every other re-render will then get a cached function

https://dev.to/milu_franz/demystifying-react-hooks-usecallback-and-usememo-1a8j

You should consider using useCallback and/or useMemo hooks in the following situations:

1. Processing large amounts of data
2. Working with interactive graphs and charts
3. Implementing animations
4. Incorporating component lazy loading (useMemo specifically)

When a component is re-rendered, it creates new instances of all objects, including all the functions in it.
