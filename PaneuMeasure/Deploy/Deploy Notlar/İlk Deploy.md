React Native'de bir APK oluşturmak için aşağıdaki adımları takip edebilirsiniz:

---

### 1. **Proje Hazırlığı**

- Projenizin tüm kodlarını test edin ve doğru çalıştığından emin olun.
- Android tarafındaki `build.gradle` ve `app.json` dosyalarını kontrol edin. Özellikle:
    - **`package` adı** (`applicationId`) benzersiz ve doğru olmalı.
    - `minSdkVersion` ve `targetSdkVersion` gibi sürüm bilgileri doğru ayarlanmalı.

---

### 2. **Keystore Dosyası Oluşturma (Signed APK için)**

Signed bir APK oluşturmak istiyorsanız bir keystore dosyası oluşturmanız gerekir:

1. **Keystore Oluşturma Komutu:**
    
    ```bash
    keytool -genkey -v -keystore my-release-key.keystore -keyalg RSA -keysize 2048 -validity 10000 -alias my-key-alias
    ```
    
2. Komut çalıştırıldığında aşağıdaki bilgileri doldurmanız istenecektir:
    - Ad, kuruluş birimi, kuruluş adı, ülke kodu vb.
    - Bir parola belirleyin ve not edin.
3. `my-release-key.keystore` dosyasını güvenli bir yere kaydedin.

---

### 3. **Keystore Dosyasını Projeye Tanıtma**

- `android/app` klasöründe bir `gradle.properties` dosyası oluşturun (eğer yoksa).
- İçine aşağıdaki bilgileri ekleyin:
    
    ```properties
    MYAPP_UPLOAD_STORE_FILE=my-release-key.keystore
    MYAPP_UPLOAD_KEY_ALIAS=my-key-alias
    MYAPP_UPLOAD_STORE_PASSWORD=parolanız
    MYAPP_UPLOAD_KEY_PASSWORD=parolanız
    ```
    
- `android/app/build.gradle` dosyasını açın ve aşağıdaki kodları kontrol edin:
    
    ```gradle
    signingConfigs {
        release {
            storeFile file(MYAPP_UPLOAD_STORE_FILE)
            storePassword MYAPP_UPLOAD_STORE_PASSWORD
            keyAlias MYAPP_UPLOAD_KEY_ALIAS
            keyPassword MYAPP_UPLOAD_KEY_PASSWORD
        }
    }
    
    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled false // İsteğe bağlı, proguard kullanacaksanız ayarlayın.
            shrinkResources false
        }
    }
    ```
    

---

### 4. **APK Oluşturma**

Terminalden aşağıdaki komutları çalıştırın:

1. **Android Klasörüne Girin:**
    
    ```bash
    cd android
    ```
    
2. **Gradle ile Build İşlemini Başlatın:**
    
    ```bash
    ./gradlew assembleRelease
    ```
    
    - Windows kullanıyorsanız:
        
        ```bash
        gradlew assembleRelease
        ```
        

---

### 5. **Oluşan APK Dosyasını Bulma**

- APK dosyanız `android/app/build/outputs/apk/release/` klasöründe olacaktır.
- `app-release.apk` adında bir dosya göreceksiniz.

---

### 6. **Test Etme**

- APK dosyasını telefonunuza yükleyin ve test edin.
- Eğer bir sorun yaşarsanız logları kontrol edin:
    
    ```bash
    adb logcat
    ```
    

---

### 7. **Google Play'e Yükleme (Opsiyonel)**

- Google Play için bir **AAB (Android App Bundle)** dosyası oluşturmak isterseniz:
    
    ```bash
    ./gradlew bundleRelease
    ```
    
    Bu işlem sonucunda `android/app/build/outputs/bundle/release/` klasöründe bir `.aab` dosyası oluşacaktır.

---

Eğer adımlarda bir sorunla karşılaşırsanız, detay vermeniz halinde yardımcı olabilirim. 😊