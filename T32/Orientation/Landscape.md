React Native'de bir uygulamayı sadece landscape modunda çalıştırmak için hem iOS hem de Android platformlarında bazı yapılandırmalar yapmanız gerekecek. Aşağıda adım adım bu işlemleri nasıl yapacağınızı anlatacağım.

### iOS için:

1. **Xcode Ayarları**:
   - Xcode'da projenizi açın (`.xcworkspace` dosyasını).
   - `General` sekmesine gidin.
   - `Deployment Info` bölümünde, `Device Orientation` kısmında sadece `Landscape Left` ve `Landscape Right` seçeneklerini işaretleyin. `Portrait` ve `Upside Down` seçeneklerini işaretlemeyin.

2. **Info.plist Dosyası**:
   - `Info.plist` dosyasını açın.
   - `UISupportedInterfaceOrientations` anahtarına aşağıdaki değerleri ekleyin:
     ```xml
     <key>UISupportedInterfaceOrientations</key>
     <array>
         <string>UIInterfaceOrientationLandscapeLeft</string>
         <string>UIInterfaceOrientationLandscapeRight</string>
     </array>
     ```

### Android için:

1. **AndroidManifest.xml Dosyası**:
   - `android/app/src/main/AndroidManifest.xml` dosyasını açın.
   - `MainActivity` tanımında, `android:screenOrientation` özniteliğini `landscape` olarak ayarlayın:
     ```xml
     <activity
         android:name=".MainActivity"
         android:label="@string/app_name"
         android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
         android:screenOrientation="landscape"
         android:windowSoftInputMode="adjustResize">
         <intent-filter>
             <action android:name="android.intent.action.MAIN" />
             <category android:name="android.intent.category.LAUNCHER" />
         </intent-filter>
     </activity>
     ```

Bu ayarları yaptıktan sonra, uygulamanız sadece landscape modunda çalışacaktır. Projenizi yeniden derleyip çalıştırarak değişikliklerin uygulandığından emin olabilirsiniz.

### React Native Config:

Bazı durumlarda, React Native uygulamanızda belirli ekranlar için yönlendirme kontrolü yapmak isterseniz, `react-native-orientation-locker` gibi kütüphaneleri kullanabilirsiniz. Ancak, sadece genel uygulama yönlendirmesi için yukarıdaki adımlar yeterli olacaktır.

Her iki platformda da bu değişiklikleri yaptıktan sonra uygulamanızın sadece landscape modunda çalışması gerektiğini göreceksiniz.