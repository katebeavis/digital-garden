# Handling Text Input

`TextInput` allows a user to enter text. It has an `onChangeText` prop that takes a function to be called every time the text is changed, and an `onSubmitEditing` proop that takes a function to be called when the text is submitted.

In the example below, every time a user enters the `onChangeText` function is called which sets the `text` state to what has been inputted. The `Text` component then displays the `text` state. Additional props such as `onFocus` enable additional functionality

```
import React, {useState} from 'react';
import {SafeAreaView, StyleSheet, View, Text, TextInput} from 'react-native';

const App = () => {
  const [text, setText] = useState('');
  const [borderWidth, setBorderWidth] = useState(0);
  const [borderColor, setBorderColor] = useState('transparent');

  const setBorder = () => {
    setBorderWidth(1);
    setBorderColor('blue');
  };

  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.view}>
        <TextInput
          placeholder={'Enter your text here'}
          onChangeText={text => setText(text)}
          style={{
            height: 40,
            borderWidth: borderWidth,
            borderColor: borderColor,
          }}
          onSubmitEditing={() => console.log('text submitted')}
          onFocus={() => setBorder()}
        />
        <Text style={styles.text}>{text}</Text>
      </View>
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  view: {
    padding: 10,
  },
  text: {
    fontSize: 42,
  },
});

export default App;
```
