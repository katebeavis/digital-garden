# Platform

React Native is designed to enable you to write code once for both ios and Android. However, there are some instances where the code works differently on each operating system

To get around this, you can use `platform`

```
import { Platform } from 'react-native'

const myFunction = Platform.select({
    ios: () => console.log('Hello iOS'),
    android: () => console.log('Hello Android'),
    default: () => console.log('Hey everyone else'),
})
```

Different styles can be added too

```
import { StyleSheet, Platform } from 'react-native'

/* Your component here */

const styles = StyleSheet.create({
    container: {
        ...Platform.select({
            ios: {
                marginBottom: 16,
            },
            android: {
                marginBottom: 8,
            },
        }),
    },
})
```

https://react.christmas/2020/1

https://reactnative.dev/docs/platform-specific-code
