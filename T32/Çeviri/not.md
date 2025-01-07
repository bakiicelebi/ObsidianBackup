React Native'de bir tuş ile tüm metinleri çevirmek için birden fazla dil desteği ve uluslararasılaştırma (i18n) kütüphanelerini kullanabilirsiniz. Yaygın olarak kullanılan kütüphanelerden biri `react-native-i18n` veya `i18next`'dir. İşte nasıl yapabileceğinize dair temel bir örnek:

1. **Kütüphaneleri Yükleyin:**

   ```sh
   npm install react-native-i18n
   npm install --save i18next react-i18next
   ```

2. **Dil Dosyalarınızı Oluşturun:**

   Projenizin kök dizininde bir `locales` klasörü oluşturun ve farklı diller için JSON dosyaları oluşturun.

   `locales/en.json`:
   ```json
   {
     "hello": "Hello",
     "welcome": "Welcome"
   }
   ```

   `locales/tr.json`:
   ```json
   {
     "hello": "Merhaba",
     "welcome": "Hoşgeldiniz"
   }
   ```

3. **i18n Konfigürasyonunu Ayarlayın:**

   Projenizin kök dizininde bir `i18n.js` dosyası oluşturun ve aşağıdaki kodu ekleyin:

   ```javascript
   import i18n from 'i18next';
   import { initReactI18next } from 'react-i18next';
   import en from './locales/en.json';
   import tr from './locales/tr.json';

   i18n
     .use(initReactI18next)
     .init({
       resources: {
         en: {
           translation: en
         },
         tr: {
           translation: tr
         }
       },
       lng: 'en', // Varsayılan dil
       fallbackLng: 'en',
       interpolation: {
         escapeValue: false
       }
     });

   export default i18n;
   ```

4. **Ana Bileşeninizi Ayarlayın:**

   `App.js` dosyanızda dil değişimini sağlayacak bir buton ekleyin.

   ```javascript
   import React, { useState } from 'react';
   import { View, Text, Button } from 'react-native';
   import { useTranslation } from 'react-i18next';
   import './i18n';

   const App = () => {
     const { t, i18n } = useTranslation();
     const [language, setLanguage] = useState('en');

     const changeLanguage = (lng) => {
       i18n.changeLanguage(lng);
       setLanguage(lng);
     };

     return (
       <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
         <Text>{t('hello')}</Text>
         <Text>{t('welcome')}</Text>
         <Button
           title="Change to Turkish"
           onPress={() => changeLanguage('tr')}
         />
         <Button
           title="Change to English"
           onPress={() => changeLanguage('en')}
         />
       </View>
     );
   };

   export default App;
   ```

Bu şekilde, "Change to Turkish" düğmesine bastığınızda dil Türkçe'ye, "Change to English" düğmesine bastığınızda dil İngilizce'ye değişecektir. Metinler otomatik olarak seçilen dile göre güncellenecektir. 

Bu, React Native'de temel bir dil değiştirme uygulamasıdır ve daha karmaşık ihtiyaçlarınız için ek ayarlar ve kütüphaneler kullanılabilir.


https://chatgpt.com/share/0f43331f-035b-4c43-a977-6899df4253d1