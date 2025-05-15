### 🔑 **Sık Kullanılan JPA Sorgu Metodu Örnekleri**

#### 1. `And` – ve

java

KopyalaDüzenle

`List<User> findByAgeAndCity(int age, String city);`

➡ Yaşı belirli olan ve şehir bilgisi eşleşen kullanıcıları getirir.

---

#### 2. `Or` – veya

java

KopyalaDüzenle

`List<User> findByAgeOrCity(int age, String city);`

➡ Yaşı ya da şehir bilgisi eşleşen kullanıcıları getirir.

---

#### 3. `Is` / `Equals` – eşittir

java

KopyalaDüzenle

`User findByEmail(String email); // veya User findByEmailIs(String email);`

``` java
List<User> findByAgeEquals(int age);
List<User> findByAgeIs(int age);
List<User> findByAgeIsEqualTo(int age);`
```


➡ Email bilgisi eşleşen kullanıcıyı getirir.

---

#### 4. `Between` – iki değer arasında

java

KopyalaDüzenle

`List<User> findByAgeBetween(int start, int end);`

➡ Yaşı belirtilen aralıkta olan kullanıcıları getirir.

---

#### 5. `LessThan` – küçük

java

KopyalaDüzenle

`List<User> findByAgeLessThan(int age);`

➡ Yaşı belirtilenden küçük olan kullanıcıları getirir.

---

#### 6. `GreaterThan` – büyük

java

KopyalaDüzenle

`List<User> findByAgeGreaterThan(int age);`

➡ Yaşı belirtilenden büyük olan kullanıcıları getirir.

---

#### 7. `Like` – benzer

java

KopyalaDüzenle

`List<User> findByNameLike(String name);`

➡ İsmi verilen değeri içeren kullanıcıları getirir. Örn: `%Ali%`

---

#### 8. `StartingWith` – ile başlar

java

KopyalaDüzenle

`List<User> findByNameStartingWith(String prefix);`

➡ İsmi belirtilen kelimeyle başlayan kullanıcıları getirir.

---

#### 9. `EndingWith` – ile biter

java

KopyalaDüzenle

`List<User> findByNameEndingWith(String suffix);`

➡ İsmi belirtilen kelimeyle biten kullanıcıları getirir.

---

#### 10. `Containing` – içinde geçen

java

KopyalaDüzenle

`List<User> findByNameContaining(String keyword);`

➡ İsmi içinde belirtilen kelime geçen kullanıcıları getirir.

---

#### 11. `In` – listede olan

java

KopyalaDüzenle

`List<User> findByIdIn(List<Long> ids);`

➡ ID'si verilen listedeki kullanıcıları getirir.

---

#### 12. `OrderBy` – sıralama

java

KopyalaDüzenle

`List<User> findByAgeGreaterThanOrderByNameAsc(int age);`

➡ Yaşı büyük olanları isme göre A-Z sıralar.