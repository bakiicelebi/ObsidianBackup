Tabii, işte Android ve iOS için NFC özelliklerini kullanabilmek için gerekli olan ek yapılandırmaların ayrıntılı açıklamaları:

**Android:**

1. **AndroidManifest.xml Yapılandırması:**
   AndroidManifest dosyanızda NFC ile ilgili izinleri ve özellikleri belirtmelisiniz. Bu dosya genellikle `android/app/src/main/AndroidManifest.xml` konumundadır. İzin eklemek için `uses-permission` etiketini kullanabilirsiniz:

   ```xml
   <uses-permission android:name="android.permission.NFC" />
   ```

   Ayrıca, uygulamanızın NFC etiketlerini okuyabilmesi için bir intent-filters eklemeniz gerekebilir. Bunun için `intent-filter` etiketini kullanabilirsiniz:

   ```xml
   <intent-filter>
       <action android:name="android.nfc.action.NDEF_DISCOVERED" />
       <category android:name="android.intent.category.DEFAULT" />
   </intent-filter>
   ```

   Bu intent-filter, uygulamanın NFC etiketlerini okuyabilmesini sağlar. Bu etiketlerin içeriğini okumak için gerekli olan NFC izinlerini de belirtmeniz önemlidir.

2. **Proje Bağımlılıkları:**
   NFC özelliklerini kullanmak için `react-native-nfc-manager` kütüphanesini projenize eklemelisiniz. Bu kütüphane, NFC işlemlerini yönetmek için gerekli araçları sağlar.

3. **Android SDK Sürümü:**
   Projenizin `build.gradle` dosyasında, `minSdkVersion` değerinin Android cihazlarının NFC'yi desteklediği bir sürüm olduğundan emin olun. Genellikle, en az API 19 (Android 4.4 KitKat) gereklidir:

   ```gradle
   android {
       ...
       defaultConfig {
           ...
           minSdkVersion 19
           ...
       }
   }
   ```

**iOS:**

1. **Capabilities Ayarları:**
   iOS için, Xcode projesindeki Capabilities sekmesinde NFC özelliğini etkinleştirmeniz gerekmektedir. Bunun için Xcode'u açın, projenizi seçin, ardından "Signing & Capabilities" sekmesine geçin ve "NFC Tag Reading" seçeneğini etkinleştirin.

2. **Info.plist Düzenlemeleri:**
   `Info.plist` dosyasına NFC ile ilgili birkaç düzenleme yapmanız gerekebilir. Bu dosya genellikle `ios/[Proje Adı]/Info.plist` konumundadır. NFC özelliğini kullanmak için izin eklemelisiniz:

   ```xml
   <key>NFCReaderUsageDescription</key>
   <string>Uygulama NFC etiketlerini okumak için kullanılacak.</string>
   ```

   Bu izin, kullanıcıya neden NFC'yi kullanmak istediğinizi açıklayan bir mesajdır. Bu mesajı, uygulamanızın gereksinimlerine göre özelleştirebilirsiniz.

3. **Deployment Target ve NFC Desteği:**
   Projenizin Deployment Target (Yayımlama Hedefi) değerinin iOS cihazlarının NFC'yi desteklediği bir sürüm olduğundan emin olun. Genellikle, NFC desteği iOS 11 veya daha yeni sürümlerde sunulmuştur. Bunun yanı sıra, iOS sürümüne göre NFC işlevselliğini kontrol edebilirsiniz.

Bu adımları takip ederek, React Native ile NFC özelliklerini kullanabilen bir uygulama geliştirebilir ve hem Android hem de iOS platformlarında çalışmasını sağlayabilirsiniz.



ios için bakarsın
https://www.youtube.com/watch?v=rAS-DvNUFck



örnek video
https://www.youtube.com/watch?v=6M_IqC4v8WI


PASSOS 1. yarn add react-native-nfc-manager 2. cd ios && pod install && cd .. 3. ANDROID (MANIFEST PERIMISSION) - ver no video 3.1 uses-permission android:name="android.permission.NFC" 4. IOS(INFO PLIST) - ver no video 4.1 key - NFCReaderUsageDescription string - Permissao de uso 4.1 key - com.apple.developer.nfc.readersession.iso7816.select-identifiers array string - D2760000850100 string - D2760000850101


örnek uygulama
https://github.com/revtel/react-native-nfc-rewriter


