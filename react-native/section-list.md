# SectionList

Similar to `FlatList` - but allows you to render items in sections with a header item inbetween. The data item is still an array, but each item in the array needs to be an object with a `title` (string) and a `data` (array) prop

You can also pass in a `renderSectionHeader` prop which will allow you to render a title for each section

```
import React from 'react';
import { Text, View, StyleSheet, SectionList, SafeAreaView } from 'react-native';

const Food = props => {
  return (
    <View style={styles.food}>
      <Text style={styles.text}>{props.name}</Text>
    </View>
  );
}

const FOODS = [
  { title: 'Healthy', data: ['Apples', 'Broccoli']},
  { title: 'Not so Healthy', data: ['Cookies', 'Doritos', 'Eclairs']},
];

const App = () => {
  return (
    <SafeAreaView>
      <SectionList
        sections={FOODS}
        keyExtractor={item => item}
        renderItem={data => <Food name={data.item} />}
        renderSectionHeader={({ section }) => (
          <Text style={styles.header}>{section.title}</Text>
        )}
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
    height: 200
  },
  text: {
    color: 'white',
    fontWeight: 'bold'
  },
  header: {
    backgroundColor: 'white',
    height: 40,
    paddingHorizontal: 5,
    fontSize: 24
  }
});

export default App;
```
