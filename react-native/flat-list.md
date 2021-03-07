# FlatList

If you have an array of items that you want to render, you should not use `map` as this will render every item on the screen, regardless of whether a user has scrolled down to them or not. This is not very performant. Instead, you should use `FlatList`

`FlatList `takes a minimum of three props:

- data - the array of data you want to map over
- renderItem - A fn that tells the `FlatList` how to render each individual item
- keyExtractor - A fn that gets passed an items and it's index

```
import React from 'react';
import { Text, View, StyleSheet, FlatList, SafeAreaView } from 'react-native';

const Food = props => {
  return (
    <View style={styles.food}>
      <Text style={styles.text}>{props.name}</Text>
    </View>
  );
}

const FOODS = [
  'Apples',
  'Broccoli',
  'Cookies',
  'Doritos',
  'Eclairs'
];

const App = () => {
  return (
    <SafeAreaView>
    <FlatList
      style={{ padding: 20}}
      data={FOODS}
      keyExtractor={item => item}
      renderItem={({ item }) => <Food name={item} />}
    />
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  food: {
    justifyContent: 'center',
    padding: 10,
    backgroundColor: 'teal',
    marginBottom: 10,
  },
  text: {
    color: 'white',
    fontWeight: 'bold'
  },
});

export default App;
```
