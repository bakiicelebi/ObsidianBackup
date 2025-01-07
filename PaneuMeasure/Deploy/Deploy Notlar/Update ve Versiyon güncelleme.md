Yeni bir versiyon için APK oluştururken aşağıdaki adımları takip edebilirsiniz:

---

### 1. **Versiyon Bilgisini Güncelleme**

Android uygulamanızın versiyon numarasını `android/app/build.gradle` dosyasından güncellemeniz gerekiyor.

1. **Dosyayı Açın:**  
    `android/app/build.gradle`
    
2. **Şu kısmı bulun:**
    
    ```gradle
    defaultConfig {
        applicationId "com.ornekproje" // Uygulamanızın package adı
        minSdkVersion 21
        targetSdkVersion 33
        versionCode 1
        versionName "1.0"
    }
    ```
    
3. **Güncellemeler:**
    
    - `versionCode`: Her yeni versiyon için 1 artırılmalı. Örneğin:
        
        ```gradle
        versionCode 2
        ```
        
    - `versionName`: Kullanıcıya görünen versiyon. Örneğin:
        
        ```gradle
        versionName "1.1"
        ```
        

---

### 2. **Keystore ve Build Ayarlarını Kontrol Etme**

Daha önce oluşturduğunuz keystore dosyasını ve ayarlarını tekrar kontrol edin. Bu ayarlar hâlâ geçerli olduğu için genelde değiştirmenize gerek yoktur.

---

### 3. **Yeni APK Oluşturma**

Daha önceki adımlarla aynı şekilde terminalden APK oluşturun:

```bash
cd android
./gradlew assembleRelease
```

Windows kullanıyorsanız:

```bash
gradlew assembleRelease
```

---

### 4. **APK Dosyasını Bulma**

Yeni APK dosyanız yine şu klasörde bulunur:  
`android/app/build/outputs/apk/release/`

- Dosyanın adı muhtemelen aynı olacaktır: `app-release.apk`.

---

### 5. **Google Play'e Yükleme (Opsiyonel)**

Eğer uygulamanızı Google Play Store'a yüklüyorsanız:

1. **Google Play Console**’a gidin.
2. Yeni versiyon için APK veya AAB dosyanızı yükleyin.
3. Yüklerken:
    - Versiyon kodunun (`versionCode`) önceki sürümden büyük olması gerektiğini unutmayın.
    - Kullanıcılar için değişiklik notlarını (`What's New`) ekleyin.

---

### 6. **Test Etme**

Yeni APK’yı yüklemeden önce, önceki sürümün doğru bir şekilde güncellendiğinden ve yeni versiyonda sorun olmadığından emin olmak için cihazınızda test edin:

```bash
adb install -r android/app/build/outputs/apk/release/app-release.apk
```

`-r` bayrağı eski sürümün üzerine yazılmasını sağlar.

---

### Ek Notlar

- **Debug Modunda Test:** Eğer önce debug modunda test etmek isterseniz:
    
    ```bash
    ./gradlew assembleDebug
    ```
    
    Bu işlem sonucunda `android/app/build/outputs/apk/debug/` klasöründe bir APK oluşur.
    
- **Değişiklikler:** Her versiyonda yapılan değişiklikler için bir `CHANGELOG` dosyası tutmak iyi bir pratiktir. Bu dosyada kullanıcılar için açıklamalar ve geliştirme detaylarını paylaşabilirsiniz.
    

Bu adımları takip ederek kolayca yeni bir APK oluşturabilirsiniz. 😊