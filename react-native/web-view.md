# WebView

`WebView` is a component that is used to handle opening exteral url's within the app.

`$ yarn add react-native-webview`

Create a component to handle the `WebView` component

```
import React from 'react';
import { View } from 'react-native';

import { WebView } from 'react-native-webview';

const Browser = (route) => {
    const { uri } = route.params;
    return (
        <View style={{ flex: 1 }}>
            <WebView source={{ uri }} />
        </View>
    );
};

export default Browser;
```

Add this route to your `StackNavigator`

```
<Stack.Screen
    name='Browser'
    component={Browser}
    options={(route) => ({ title: route.params.name })}
/>
```

Then you can use it in another component

```
<TouchableHighlight
    onPress={() =>
        navigation.navigate('Browser', {
            uri: 'http://www.google.com',
            name: 'Browser',
        })
    }
    underlayColor={'transparent'}
>
```
