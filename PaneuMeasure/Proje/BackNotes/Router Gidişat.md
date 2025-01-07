
## Router Gidişat

-  Ana ekranda Grup Seçimi Yapılacak olan ekran açılış olduğu için kök dizinde yer alacak
-  Bu ekranda iki farklı Stack.Group seçimi olacak
-  Birincisinde CycleBased
-  İkincisinde Henkaten/Repaired

Böylece;
- Başlangıçta Henkaten/Repair sayfaları render edilmeyecek
- Ana sayfadan yapılacak yönlendirmeler bir arada tutulacak
- CycleBased seçimi içerisinde gerektiğinde yeni bir navigasyon oluşturulmaya elverişli olunacak
- Dilendiğinde Stack.Group içerisinde nested navigasyon entegre edilebilecek
- Bu gruplar içerisinde oluşturulan navigasyonlar gerekli context yapısını içerisinde barındırabilecek. Örneğin: Ölçüm alınacak olan öğe seçildiğinde bu öğenin bilgilerini genel bir context ile saklamaktansa ölçüm sayfalarının scope'unda saklanabilecek.

- **Üstteki Örnek için detaylandırma**: /Router/Group/CycleBased/Group/ÖlçümİçinGerekliBilgilerinTutulduğuContext/ÖlçümEkranları



-> Dizin Gösterimi
/Router.tsx
Departman seçim ekranı
/Group1/CycleBased   //1.Seçim tarafı  
/Group2/Henkaten-Repair   //2.Seçim tarafı


