# useEffect

The useEffect hook allows you to perform side effects in function components

It can be thought as componentDidMount, componentDidUpdate and componentWillUnmount in one

We can run effects without cleanup and with cleanup

## Effects without clean up

Sometimes we want to run code after the DOM has
updated. E.g. updating some text on the page when a counter has changed

```
useEffect(() => {
  document.title = `You clicked ${count} times`;
})
```

The above tells React that your component needs to do something after render. It will run after the first render and every time the DOM is updated

## Effects with cleanup

Some effects require cleanup, for example a subscription, otherwise this may cause a memory leak. Cleanups are functions returned from the useEffect hook and are run when the component unmounts. Reatt also cleans up effects from the previous render before running the effects next time

```
useEffect(() => {
  // subscribe to a service
  return () => {
  // unsubscribe from a service
  }
})
```

It's important that React runs the cleanup function before running the effect again because props may have changed between rerenders and otherwise the component may try to run an effect with the old props

An example is below:

```
// Mount with { friend: { id: 100 } } props
ChatAPI.subscribeToFriendStatus(100, handleStatusChange);     // Run first effect

// Update with { friend: { id: 200 } } props
ChatAPI.unsubscribeFromFriendStatus(100, handleStatusChange); // Clean up previous effect
ChatAPI.subscribeToFriendStatus(200, handleStatusChange);     // Run next effect

// Update with { friend: { id: 300 } } props
ChatAPI.unsubscribeFromFriendStatus(200, handleStatusChange); // Clean up previous effect
ChatAPI.subscribeToFriendStatus(300, handleStatusChange);     // Run next effect

// Unmount
ChatAPI.unsubscribeFromFriendStatus(300, handleStatusChange); // Clean up last effect
```

## Hooks allow us to seperate concerns

Previously, when using component lifecycle methods, unrelated code would all be within one function as there was only one componentDidMount, componentDidUpdate and componentWillUnmount allowed per React component

As we are allowed to use multiple hooks, we can seperate code out into different hooks

```
useEffect(() => {
  document.title = `You clicked ${count} times`;
})

useEffect(() => {
  // some other code to run
})
```

Hooks let us split the code based on what it is doing rather than a lifecycle method name. React will apply every effect used by the component, in the order they were specified

## Optimizing Performance by Skipping Effects

Sometimes you only want an effect to run if something in particuar has changed. You can do this by passing an array as an optional second argument to useEffect

The below only runs when the count variable is updated

```
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count])
```

If you want to run an effect and clean it up only once (on mount and unmount), you can pass an empty array ([]) as a second argument
