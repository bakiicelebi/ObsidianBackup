Tabii, bir alışveriş sepeti örneği üzerinden Context API'yi nasıl kullanabileceğimizi göstereyim. Bu örnekte, ürünleri sepete ekleme ve çıkarma işlemlerini gerçekleştireceğiz.

### Adım 1: Proje Oluşturma

Öncelikle, yeni bir React Native projesi oluşturun:

```bash
npx react-native init ShoppingCartApp
cd ShoppingCartApp
```

### Adım 2: Context API Yapısını Oluşturma

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
import React, { createContext, useState } from 'react';

// Context oluşturma
export const CartContext = createContext();

// Provider bileşeni
export const CartProvider = ({ children }) => {
  const [cart, setCart] = useState([]);

  const addToCart = (item) => {
    setCart([...cart, item]);
  };

  const removeFromCart = (itemId) => {
    setCart(cart.filter(item => item.id !== itemId));
  };

  return (
    <CartContext.Provider value={{ cart, addToCart, removeFromCart }}>
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

- **`CartContext.js`**: Bu dosyada, alışveriş sepeti için bir Context ve Provider bileşeni oluşturduk. `useState` ile sepetin durumunu yönettik ve `addToCart` ve `removeFromCart` fonksiyonlarını tanımladık.
- **`App.js`**: Uygulamanın kök bileşeni olan `App` bileşeninde, `CartProvider` bileşenini kullanarak Context'i sağladık. `ProductList` bileşeninde ürünleri listeleyip sepete ekleme işlemini gerçekleştirdik. `Cart` bileşeninde ise sepet içeriğini listeleyip ürünleri sepetten çıkarma işlemini gerçekleştirdik.

Bu adımları takip ederek React Native'de Context API'yi kullanarak basit bir alışveriş sepeti uygulaması oluşturabilirsiniz. Bu temel yapı, daha karmaşık alışveriş sepeti senaryolarına uyarlanabilir.