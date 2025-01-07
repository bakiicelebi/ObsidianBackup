```
view: {
    position: "absolute",
    top: 0,
    left: 0,
    right: 0,
    bottom: 0,
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "transparent",
    zIndex: 1
  }
```

import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const App = () => {
  return (
    <View style={styles.container}>
      <View style={styles.background}>
        <Text style={styles.text}>Arka Plan Opasitesi Azaltılmış Metin</Text>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  background: {
    backgroundColor: 'rgba(255, 255, 255, 0.5)', // Beyaz arka plan, %50 opasite
    padding: 20,
    borderRadius: 10,
  },
  text: {
    fontSize: 24,
    fontWeight: 'bold',
  },
});

export default App;
