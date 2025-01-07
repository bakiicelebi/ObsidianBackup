React Native kullanarak bir PDF oluşturup bunu bir e-postaya eklemek için `react-native-pdf-lib` ve `react-native-email` gibi kütüphaneleri kullanabilirsiniz. İşte bu işlemi adım adım nasıl yapabileceğinizi anlatan bir rehber:

1. **Gerekli Kütüphaneleri Kurun:**
   İlk olarak, gerekli kütüphaneleri kurmanız gerekiyor. Projenizin dizininde terminal açarak şu komutları çalıştırın:

   ```bash
   npm install react-native-pdf-lib
   npm install react-native-email
   ```

2. **PDF Oluşturma Kodu:**
   PDF oluşturma işlemini bir fonksiyon içinde yapabiliriz. Aşağıdaki örnekte, fişteki bilgileri kullanarak basit bir PDF oluşturacağız:

   ```javascript
   import React from 'react';
   import { View, Button } from 'react-native';
   import { PDFDocument, rgb } from 'react-native-pdf-lib';
   import RNFS from 'react-native-fs';
   import email from 'react-native-email';

   const App = () => {

     const createPDF = async () => {
       const docsDir = await RNFS.DocumentDirectoryPath;
       const pdfPath = `${docsDir}/receipt.pdf`;

       const page = PDFDocument.create()
         .addPages(
           PDFDocument.Page.create()
             .setMediaBox(200, 200)
             .drawText('ÖRNEK İŞLETME', {
               x: 5,
               y: 180,
               color: rgb(0.95, 0.1, 0.1),
               fontSize: 15,
             })
             .drawText('Tarih: 07.05.2019 Saat: 12:30', {
               x: 5,
               y: 160,
               color: rgb(0.0, 0.0, 0.0),
               fontSize: 10,
             })
             .drawText('Satış No: 2 Satış: Nakit', {
               x: 5,
               y: 150,
               color: rgb(0.0, 0.0, 0.0),
               fontSize: 10,
             })
             .drawText('Kasiyer: Ahmet', {
               x: 5,
               y: 140,
               color: rgb(0.0, 0.0, 0.0),
               fontSize: 10,
             })
             // Diğer ürün detaylarını burada ekleyebilirsiniz
         );

       await PDFDocument.create().addPages(page).write(pdfPath);

       return pdfPath;
     };

     const handleEmail = async () => {
       const pdfPath = await createPDF();

       const to = ['example@example.com'];
       email(to, {
         subject: 'Fiş PDF',
         body: 'Bu e-posta ile fişin PDF versiyonunu bulabilirsiniz.',
         attachment: {
           path: pdfPath,
           type: 'pdf',
           name: 'receipt.pdf',
         },
       }).catch(console.error);
     };

     return (
       <View style={{ marginTop: 50 }}>
         <Button title="PDF Oluştur ve Gönder" onPress={handleEmail} />
       </View>
     );
   };

   export default App;
   ```

3. **Android için Ekstra Ayarlar:**
   Android'de dosya sistemine erişim ve e-posta gönderimi için bazı ekstra izinler eklemeniz gerekecek. `AndroidManifest.xml` dosyasına şu izinleri ekleyin:

   ```xml
   <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
   <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
   ```

4. **iOS için Ekstra Ayarlar:**
   iOS'ta dosya sistemine erişim için ekstra bir şey yapmanıza gerek yoktur, ancak e-posta gönderme işlemi için Mail uygulamasının kurulu olduğundan emin olmalısınız.

Bu adımları izledikten sonra, React Native uygulamanızda bir butona tıklayarak PDF oluşturup bunu e-posta ile gönderebilirsiniz. `react-native-pdf-lib` ve `react-native-email` kütüphanelerinin belgelerini inceleyerek daha fazla özelleştirme yapabilirsiniz


![[market-fis.jpg]]