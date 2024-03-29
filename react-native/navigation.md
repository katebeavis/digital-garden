# Navigation

Navigation in React Native apps is commonly handled by `react-navigation`

There are three types of navigation in React native - **tab navigation** **drawer navigation** and **stack navigation**

Tab navigation is the most common form of navigation in mobile apps and consists of bottom and top tabs. An of bottom navigation example in many apps is the home icon, search icon etc at the bottom of the screen. Navigating between screens is pretty instant. When the app is launched, all root pages on the bottom navigation get rendered at once

Drawer navigation is when the app has a drawer from the left or right side of the screen in order to navigate the app. Usually it consists of links. It's similar to a side bar in web based apps. Twitter is an example of an app that uses this

Stack navigation uses the concept of 'stacks' to transition between scrrens. Screens are stacked on top of each other and movement between screens adds to the stack

The whole app needs to be wrapped in `NavigationContainer` which is a component which manages our navigation tree and contains the navigation state. This component must wrap all navigators structure.

## Stack navigator

The stack navigator provides a way for your app to transition between screens and manage navigation history.

If your app uses only one stack navigator then it is conceptually similar to how a web browser handles navigation state - your app pushes an dpops items from the navigation stack as users interact with it, and this resukts in the user seeing different screens.

The most common navigator is `createStackNavigator`

## createStackNavigator

`createStackNavigator` is a function that returns an object containing 2 properties: `Screen` and `Navigator`. The `Navigator` should contain `Screen` elements as its children to define the configuration for routes.

## Specifying routes

A route can be specified by using the `Screen` component. The `Screen` component accepts a `name` props which correswponds to the name of theroute we will use to navigate, and a `component` prop which corresponds to the component it'll render. There is also an optional `options` prop that can specify some options for the navigator, such as the title to render in the header.

## Passing additional props

We can pass additional props to the screen with 2 approaches:

1. Use `React Context` and wrap the navigator with a context providor to pass the data to the screens.

2. Use a render callback for the screen instead of specifying a `component` prop.

```
import 'react-native-gesture-handler';
import * as React from 'react';
import {NavigationContainer} from '@react-navigation/native';
import {createStackNavigator} from '@react-navigation/stack';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen
          name="Home"
          component={Home}
          options={{title: 'Welcome'}}
        />
        <Stack.Screen name="Profile" component={Profile} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

## Moving between screens

<!-- TODO add backlink -->

To move between screens we use the `navigation` prop that is passed down to our screen components.

To programmatically go back you can use `navigation.goBack()`

To go back to the first screen in the stack you can use `navigation.popToTop()`

```
<Button
    title="Go to Details"
    onPress={() => navigation.navigate('Details')}
/>
```

## Passing parameters to routes

There are 2 pieces to passing data to our routes when we navigate to them:

1. Pass params to a route by putting them in an object as a second paramater to the `navigation.navigate` function: `navigation.navigate('RouteName', { /* params go here */ })`

2. Read the params in your screen component: `route.params`

```
const HomeScreen = ({ navigation }) => {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>Home Screen</Text>
      <Button
        title="Go to Details"
        onPress={() => {
          /* 1. Navigate to the Details route with params */
          navigation.navigate('Details', {
            itemId: 86,
            otherParam: 'anything you want here',
          });
        }}
      />
    </View>
  );
}

const DetailsScreen = ({ route, navigation }) => {
  /* 2. Get the param */
  const { itemId, otherParam } = route.params;
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>Details Screen</Text>
      <Text>itemId: {JSON.stringify(itemId)}</Text>
      <Text>otherParam: {JSON.stringify(otherParam)}</Text>
      <Button
        title="Go to Details... again"
        onPress={() =>
          navigation.push('Details', {
            itemId: Math.floor(Math.random() * 100),
          })
        }
      />
      <Button title="Go to Home" onPress={() => navigation.navigate('Home')} />
      <Button title="Go back" onPress={() => navigation.goBack()} />
    </View>
  );
}
```

## Updating params

Screens can also update their params, like they can update their state. The `navigation.setParams`

You can also pass some initial params to a screen. If you didn't specify any params when navigating to the screen, the initial params will be used.

## Passing params to a previous screen

You can also pass params to a previous screen.
