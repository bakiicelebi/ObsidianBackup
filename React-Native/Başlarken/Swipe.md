https://github.com/jshanson7/react-native-swipeable
**İşte Swipeable bileşenini React Native projenizde nasıl kullanabileceğiniz:**

**1. Kurulum:**

- Henüz yapmadıysanız, `react-native-gesture-handler` paketini kurun:

Bash

```
npm install react-native-gesture-handler
```

import React from 'react';

import { View, Text, StyleSheet, Dimensions } from 'react-native';

import { GestureHandlerRootView } from 'react-native-gesture-handler';

  

import Swipeable from 'react-native-gesture-handler/Swipeable';

  

const App = () => {

  const width = Dimensions.get('window').width

  const styles = StyleSheet.create({

    container: {

      backgroundColor: 'lightblue',

      padding: 20,

    },

    leftActions: {

      backgroundColor: 'lightgreen',

      flex: 0.5,

      justifyContent: 'center',

      alignItems: 'center',

    },

  });

  

  return (

    <GestureHandlerRootView style={{ flex: 1 }}>

      <Swipeable overshootRight={false} renderRightActions={() => <View style={styles.leftActions}><Text>AAA</Text></View>}>

        <View style={styles.container}>

          <Text>sas</Text>

        </View>

      </Swipeable>

    </GestureHandlerRootView>

  );

};

  

export default App;