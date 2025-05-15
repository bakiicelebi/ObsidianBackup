### 📌 **Query Methods Nedir?**

- Spring Data JPA, metot isimlerine göre otomatik SQL sorguları oluşturur.
    
- Bu yöntemle manuel olarak SQL yazmaya gerek kalmaz.
    
- En güçlü sorgulama yöntemlerinden biridir.
    
- Sorgular, entity sınıfındaki alan adları kullanılarak yazılır.
    
- Repository katmanında sadece metot tanımlayarak sorgulama yapılabilir.
    

---

### ⚠️ **Dikkat Edilmesi Gereken Noktalar**

- Sorgu metodunun isminde sadece entity sınıfındaki değişken adları kullanılabilir.
    
- Veritabanındaki tablo veya kolon isimleri değil, Java sınıfındaki alan adları esas alınır.
    
- Metot isminde bazı özel anahtar kelimeler kullanılabilir.
    
- Bu anahtar kelimeler arasında “ve”, “veya”, “küçüktür”, “büyüktür”, “arasında”, “içerir”, “başlar”, “sıralı” gibi anlamlara gelen kalıplar vardır.
    
- Bu kurallar dışına çıkılırsa Spring hata verir veya metodu tanıyamaz.
    

---

### 🧠 **Nasıl Çalışır?**

- Spring, metot ismine bakarak arka planda uygun SQL cümlesini oluşturur.
    
- Metotta yazılan alan adları ve kurallar, SQL’in “where” şartlarını belirler.
    
- Metot parametreleri, sorguya yerleştirilecek değerleri temsil eder.
    
- Bu yapı sayesinde çok az kod yazarak güçlü ve dinamik sorgular yapılabilir.