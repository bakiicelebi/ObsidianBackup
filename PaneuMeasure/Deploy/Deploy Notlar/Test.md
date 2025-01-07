Test yapmak için adımları detaylı şekilde açıklıyorum:

---

### 1. **ADB'nin Kurulu Olduğundan Emin Olun**

ADB (Android Debug Bridge), cihazınıza APK yüklemek ve test etmek için gereklidir.

#### ADB'yi Kurmak:

1. Android Studio yüklüyse, ADB zaten kurulu olacaktır.
2. **ADB'yi manuel kurmak isterseniz:**
    - [Android Platform Tools](https://developer.android.com/studio/releases/platform-tools) sayfasından indirin.
    - İndirdiğiniz klasörü sistem PATH'ine ekleyin.

#### ADB'yi Test Etmek:

Terminal veya komut istemcisinde şu komutu çalıştırın:

```bash
adb devices
```

Cihazınız bağlıysa bir liste görmelisiniz. Örneğin:

```
List of devices attached
emulator-5554   device
```

---

### 2. **Cihazınızı veya Emülatörü Bağlayın**

#### Fiziksel Cihaz:

1. **USB hata ayıklamayı etkinleştirin:**
    - Telefonunuzdan **Geliştirici Seçenekleri**ni açın.
    - **USB Hata Ayıklama**yı etkinleştirin.
2. Telefonunuzu USB ile bilgisayara bağlayın.

#### Emülatör:

- Android Studio'dan bir emülatör başlatabilirsiniz.

---

### 3. **APK Dosyasını Yükleyin**

Terminal veya komut istemcisinde şu komutu çalıştırın:

```bash
adb install -r android/app/build/outputs/apk/release/app-release.apk
```

- **`-r` Bayrağı:** Eski sürümü kaldırmadan üzerine yazar.
- Eğer farklı bir sürümle sorun yaşarsanız, eski uygulamayı manuel olarak kaldırıp tekrar yükleyebilirsiniz:
    
    ```bash
    adb uninstall com.ornekproje
    adb install android/app/build/outputs/apk/release/app-release.apk
    ```
    

---

### 4. **Uygulamayı Test Edin**

- Uygulama yüklendikten sonra cihazda uygulamayı çalıştırın.
- Geliştirici konsolunda logları izlemek için şu komutu kullanın:
    
    ```bash
    adb logcat
    ```
    
    Özellikle hata mesajlarını (`E/` ile başlayan) kontrol edin.

---

### 5. **Özelleştirilmiş Test Senaryoları**

- **Görsel Kontroller:** Tüm ekranların doğru çalıştığından emin olun.
- **Performans:** Gecikme, çökme veya performans sorunları olup olmadığını test edin.
- **Versiyon Güncellemesi:** Eski bir versiyon yüklüyse, yeni APK'nın üzerine yazılmasını ve sorunsuz bir şekilde güncellenmesini kontrol edin.
- **Kullanıcı İşlevleri:** Kullanıcı etkileşimleri (butonlar, girişler) ve veri işleme akışlarını kontrol edin.

---

### 6. **Log Kayıtlarını Kaydetme**

Test sırasında oluşan hataları analiz etmek için logları bir dosyaya kaydedebilirsiniz:

```bash
adb logcat > logs.txt
```

---

Testler tamamlandığında, her şey düzgün çalışıyorsa uygulamanız yeni versiyona hazır demektir! 😊