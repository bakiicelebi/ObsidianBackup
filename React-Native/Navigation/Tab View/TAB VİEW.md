https://reactnavigation.org/docs/tab-view

Object.fromEntries( data.map(item => [item.id.toString(), () => <TabContent title={item.title} />]) )
bu objeyi ikili yapıyo

`Object.fromEntries` yöntemi, bir dizi çiftlerden oluşan bir listeyi kullanarak bir nesne oluşturur. Bu yöntem, dizi çiftlerini kullanarak bir nesne oluşturmanın tersidir.

Normalde, bir nesne oluşturmak için dizi çiftlerini kullanabilirsiniz:

```javascript
const entries = [['key1', 'value1'], ['key2', 'value2']];
const obj = Object.fromEntries(entries);
console.log(obj); // Çıktı: { key1: 'value1', key2: 'value2' }
```

Burada `entries` adlı bir dizi çiftleri dizisi var. Bu dizi çiftlerini kullanarak `Object.fromEntries` yöntemi ile bir nesne oluşturuluyor.

Örneğin, bir dizi çiftlerinden oluşan bir liste var ve bu listeyi nesneye dönüştürmek istiyorsanız, `Object.fromEntries` kullanabilirsiniz. Bu örnekte, dizi çiftlerini kullanarak her bir tab için bir anahtar-değer çifti oluşturuyoruz:

```javascript
const data = [
    { id: 1, title: 'Tab 1' },
    { id: 2, title: 'Tab 2' },
    { id: 3, title: 'Tab 3' },
];

const routeEntries = data.map(item => [item.id.toString(), () => <TabContent title={item.title} />]);

const renderScene = Object.fromEntries(routeEntries);
```

Bu şekilde, `renderScene` objesi her bir tab için bir anahtar-değer çiftine sahip olur, anahtarlar tabların id'leri (dize olarak) ve değerler ise her bir tab için içeriği oluşturan bir fonksiyondur. Bu `renderScene` objesi, `TabView` bileşeninde tabları oluşturmak için kullanılır.

const renderScene = SceneMap( Object.fromEntries( data.map((item: any) => [item.id.toString(), () => <TabContent title={item.title} />]) ) );  .tsx

**DİKKAT ET**

 LOG  VirtualizedList: You have a large list that is slow to update - make sure your renderItem function renders components that follow React performance best practices like PureComponent, shouldComponentUpdate, etc. {"contentLength": 2304, "dt": 589, "prevDt": 848}




