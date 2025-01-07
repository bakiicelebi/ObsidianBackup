import React, { useState } from 'react';
import { TouchableOpacity, Text, Alert } from 'react-native';

const YourComponent = (props) => {
  const [count, setCount] = useState(0);
  const [lastPress, setLastPress] = useState(0);

  const handlePress = () => {
    const currentTime = new Date().getTime();
    const doublePressDelay = 300; // İki tıklama arasındaki minimum gecikme süresi (milisaniye cinsinden)

    if (currentTime - lastPress <= doublePressDelay) {
      // İki kez peş peşe tıklandığında
      setCount(count + 1);
      if ((count + 1) % 2 === 0) {
        Alert.alert('Başlık');
      }
    } else {
      // İlk tıklama
      setCount(1);
    }

    // Son tıklamanın zamanını güncelle
    setLastPress(currentTime);
  };

  return (
    <TouchableOpacity onPress={handlePress}>
      <Text numberOfLines={1} ellipsizeMode="tail" style={styles.taskText}>{props.task.task}</Text>
    </TouchableOpacity>
  );
};

export default YourComponent;
