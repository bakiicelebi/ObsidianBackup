
### **İş Akışı Adımları**

#### 1. **Sisteme Giriş (Authentication)**

- **Admin/Çalışan/Müşteri** giriş yapar.
- Giriş yapan kullanıcıya göre yetkiler atanır (Admin, Manager, User, Guest).
- Hatalı giriş durumunda hata mesajı görüntülenir.

#### 2. **Hizmetlerin Tanımlanması (Admin/Manager)**

- Yeni hizmet kategorileri ve hizmetler eklenir.
- Hizmetin fiyatı ve süresi belirtilir.
- Gerekirse promosyonlar tanımlanır.

#### 3. **Çalışan Yönetimi (Admin)**

- Çalışanlar sisteme eklenir (isim, pozisyon, maaş, uzmanlık alanları, çalışma saatleri).
- Çalışanların salon ile ilişkisi kurulur.
- Çalışan uygunluğu düzenlenir.

#### 4. **Randevu Alma (Müşteri)**

- Müşteri, giriş yaptıktan sonra:
    - Hizmet seçer.
    - Çalışan seçer (isteğe bağlı).
    - Randevu tarih ve saatini belirler.
- Sistem uygunluk kontrolü yapar:
    - Uygun değilse başka zaman önerir.
    - Uygunsa randevu oluşturulur.
- Randevu onay mekanizması çalışır.

#### 5. **Hizmetin Sunulması**

- Çalışan belirlenen saatte müşteriyi kabul eder.
- Hizmet tamamlanınca sistemde işaretlenir.

#### 6. **Ödeme ve Gelir Takibi**

- Hizmet tamamlandıktan sonra:
    - Ödeme alınır (nakit/kredi kartı).
    - Ödeme bilgisi sisteme kaydedilir.
- Gelir günlük/haftalık/aylık olarak raporlanır.

#### 7. **Yapay Zeka Saç Modeli/Renk Önerisi**

- Müşteri sisteme fotoğraf yükler.
- Yapay zeka, fotoğrafı analiz eder.
- Saç modeli veya renk önerisi sunulur.

#### 8. **Geri Bildirim ve Yorumlar**

- Müşteri aldığı hizmet için yorum yapar.
- Yorumlar değerlendirilir ve istatistiklerde kullanılır.

#### 9. **Raporlama ve Yönetim (Admin/Manager)**

- Sistemden:
    - Gelir raporları alınır.
    - Çalışan performansı incelenir.
    - Popüler hizmetler analiz edilir.
- Gerekirse yeni kararlar alınır (fiyat değişiklikleri, promosyonlar vb.).

---

### **İş Akışı Rol Bazlı Özet**

| Rol         | Yetki ve İşlem                                                |
| ----------- | ------------------------------------------------------------- |
| **Admin**   | Hizmet, çalışan, müşteri yönetimi, raporlar, sistem ayarları. |
| **Manager** | Çalışan uygunluğu ve randevu yönetimi.                        |
| **User**    | Hizmet seçimi, randevu oluşturma, ödeme yapma.                |
| **Guest**   | Hizmetleri ve salon bilgilerini inceleme (kayıt olmadan).     |

---

### Görsel İş Akışı

Bunu görselleştirmek için bir diyagram çizmek istiyorsanız, **başlangıçtan bitişe** şu şekilde düşünebiliriz:

1. Giriş -> Yetki Kontrolü
2. Hizmet ve Çalışan Yönetimi
3. Randevu Oluşturma (Müşteri)
4. Hizmet Sunumu ve Tamamlama
5. Ödeme ve Gelir Kaydı
6. Yapay Zeka Önerisi
7. Geri Bildirim ve Analiz

Eğer görsel bir diyagram isterseniz, hemen bir şema oluşturabilirim. İlgili şemayı da istediğiniz gibi düzenleyebiliriz. 😊