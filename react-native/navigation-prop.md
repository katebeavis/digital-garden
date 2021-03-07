# Navigation prop

Each screen component is automatically passed a `navigation` prop. This prop provides convenience functions that dispatch navigation actions:

- `navigation`

  - `navigate` - go to another screen, figures out the action it needs to take to do it
  - `reset` - wipe the navigator state and replace it with a new route
  - `goBack` - close active screen and move back in the stack
  - `setParams` - make changes to route's params
  - `dispatch` - send an action object to update the navigation state
  - `setOptions` - update the screen's options
  - `isFocused` - check whether the screen is focused
  - `addListener` - subscribe to updates to events from the navigators

  Only `screen` components are passed the `navigation` prop. Child components of screen components are not passed it. However, if you wish to access the navigation prop in another component,, you can use the `useNavigation` hook
