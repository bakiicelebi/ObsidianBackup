Tabii ki, AsyncStorage ve reducer kullanarak daha gelişmiş bir alışveriş sepeti uygulaması oluşturabiliriz. Bu adımda, Redux benzeri bir yapı kullanarak global durum yönetimi yapacağız. AsyncStorage, verileri kalıcı olarak depolamak için kullanılacak.

### Adım 1: Proje Oluşturma ve Kütüphaneleri Kurma

Öncelikle, yeni bir React Native projesi oluşturun ve gerekli kütüphaneleri yükleyin:

```bash
npx react-native init ShoppingCartApp
cd ShoppingCartApp
npm install @react-native-async-storage/async-storage
```

### Adım 2: Context API ve Reducer Yapısını Oluşturma

#### a. `context` Klasörü ve `CartContext.js` Dosyası Oluşturma

Proje kök dizininde bir `context` klasörü oluşturup, bu klasörün içinde `CartContext.js` dosyasını oluşturalım:

```bash
mkdir context
cd context
touch CartContext.js
```

#### b. `CartContext.js` İçeriğini Yazma

`CartContext.js` dosyasını şu şekilde yapılandırın:

```javascript
import React, { createContext, useReducer, useEffect } from 'react';
import AsyncStorage from '@react-native-async-storage/async-storage';

// Context oluşturma
export const CartContext = createContext();

const initialState = {
  cart: [],
};

// Reducer fonksiyonu
const cartReducer = (state, action) => {
  switch (action.type) {
    case 'ADD_TO_CART':
      return { ...state, cart: [...state.cart, action.payload] };
    case 'REMOVE_FROM_CART':
      return { ...state, cart: state.cart.filter(item => item.id !== action.payload) };
    case 'SET_CART':
      return { ...state, cart: action.payload };
    default:
      return state;
  }
};

// Provider bileşeni
export const CartProvider = ({ children }) => {
  const [state, dispatch] = useReducer(cartReducer, initialState);

  useEffect(() => {
    const loadCart = async () => {
      const cartData = await AsyncStorage.getItem('cart');
      if (cartData) {
        dispatch({ type: 'SET_CART', payload: JSON.parse(cartData) });
      }
    };
    loadCart();
  }, []);

  useEffect(() => {
    const saveCart = async () => {
      await AsyncStorage.setItem('cart', JSON.stringify(state.cart));
    };
    saveCart();
  }, [state.cart]);

  const addToCart = (item) => {
    dispatch({ type: 'ADD_TO_CART', payload: item });
  };

  const removeFromCart = (itemId) => {
    dispatch({ type: 'REMOVE_FROM_CART', payload: itemId });
  };

  return (
    <CartContext.Provider value={{ cart: state.cart, addToCart, removeFromCart }}>
      {children}
    </CartContext.Provider>
  );
};
```

### Adım 3: `App.js` Dosyasını Düzenleme

Projenizin kök dizininde bulunan `App.js` dosyasını düzenleyin:

```javascript
import React from 'react';
import { View, Text, Button, FlatList } from 'react-native';
import { CartProvider, CartContext } from './context/CartContext';

const ProductList = () => {
  const products = [
    { id: 1, name: 'Product 1' },
    { id: 2, name: 'Product 2' },
    { id: 3, name: 'Product 3' },
  ];

  const { addToCart } = React.useContext(CartContext);

  return (
    <View>
      <Text>Product List</Text>
      {products.map(product => (
        <View key={product.id} style={{ marginVertical: 5 }}>
          <Text>{product.name}</Text>
          <Button title="Add to Cart" onPress={() => addToCart(product)} />
        </View>
      ))}
    </View>
  );
};

const Cart = () => {
  const { cart, removeFromCart } = React.useContext(CartContext);

  return (
    <View>
      <Text>Shopping Cart</Text>
      <FlatList
        data={cart}
        keyExtractor={(item) => item.id.toString()}
        renderItem={({ item }) => (
          <View style={{ marginVertical: 5 }}>
            <Text>{item.name}</Text>
            <Button title="Remove" onPress={() => removeFromCart(item.id)} />
          </View>
        )}
      />
    </View>
  );
};

const App = () => {
  return (
    <CartProvider>
      <View style={{ flex: 1, padding: 20 }}>
        <ProductList />
        <Cart />
      </View>
    </CartProvider>
  );
};

export default App;
```

### Adım 4: Projeyi Çalıştırma

```bash
npx react-native run-android
# veya
npx react-native run-ios
```

### Açıklamalar

- **`CartContext.js`**: Bu dosyada, alışveriş sepeti için bir Context ve Reducer yapılandırdık. `useReducer` ile sepetin durumunu yönettik ve `useEffect` ile AsyncStorage'dan verileri yükleyip kaydettik. `addToCart` ve `removeFromCart` fonksiyonlarını tanımladık.
- **`App.js`**: Uygulamanın kök bileşeni olan `App` bileşeninde, `CartProvider` bileşenini kullanarak Context'i sağladık. `ProductList` bileşeninde ürünleri listeleyip sepete ekleme işlemini gerçekleştirdik. `Cart` bileşeninde ise sepet içeriğini listeleyip ürünleri sepetten çıkarma işlemini gerçekleştirdik.

Bu adımları takip ederek React Native'de AsyncStorage ve reducer kullanarak kalıcı bir alışveriş sepeti uygulaması oluşturabilirsiniz.