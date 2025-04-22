Tabii ki Baki! İşte sana React'ta `useMemo`, `useCallback`, `React.memo` ve benzeri konularda **ne zaman neyi kullanmalıyım?** diye düşüneceğin zamanlar için süper sade ve net bir **cheat sheet** 🧠💡

---

## 🧩 React Performans Cheat Sheet

### 🔹 `React.memo(Component)`

**Ne yapar?**  
Bir bileşen, props'ları değişmediyse yeniden render edilmez.

**Ne zaman kullan?**

- Bileşen büyük veya sık sık render ediliyor ama props sabitse
    
- Performans kazancı istiyorsan
    

✅ Örnek:

```tsx
const MyComponent = React.memo(({ title }) => {
  console.log("render");
  return <div>{title}</div>;
});
```

---

### 🔹 `useCallback(() => {}, [deps])`

**Ne yapar?**  
Fonksiyonun referansını sabit tutar. Her render'da yeni fonksiyon oluşturulmasını engeller.

**Ne zaman kullan?**

- Fonksiyonu çocuk bileşene `prop` olarak geçiyorsan
    
- `React.memo` kullanılmış çocuk bileşende gereksiz renderları önlemek istiyorsan
    

✅ Örnek:

```tsx
const handleClick = useCallback(() => {
  console.log("Tıklandı");
}, []);
```

---

### 🔹 `useMemo(() => değer, [deps])`

**Ne yapar?**  
Bir değeri (örneğin hesaplama sonucu) yeniden hesaplamamak için hafızada tutar.

**Ne zaman kullan?**

- Ağır işlem yapan hesaplamalarda (`filter`, `sort`, `reduce` gibi)
    
- Referansı değişmeyen obje/dizi göndermek istiyorsan
    

✅ Örnek:

```tsx
const sortedList = useMemo(() => {
  return list.sort((a, b) => a - b);
}, [list]);
```

---

## 🎯 Ne Zaman Hangisini Kullanayım?

|Durum|Kullan|
|---|---|
|Fonksiyon her render'da yeniden oluşuyor ve bu `React.memo` bileşene gidiyor|`useCallback`|
|Ağır bir işlem sonucu hesaplanan bir değer her render’da tekrar hesaplanıyor|`useMemo`|
|Bileşen aynı props ile tekrar tekrar render oluyor|`React.memo`|
|State ya da props değişmediği halde alt bileşen render oluyor|`React.memo` + `useCallback` / `useMemo`|

---

## 🚨 Ne Zaman Kullanma?

- Eğer render süren kısaysa ve çok karmaşık işlem yoksa, `useMemo` ve `useCallback` **gereksiz yere** karmaşıklık ve hafıza tüketimi yaratabilir.
    
- "Her yerde kullanayım" düşüncesi **performansı artırmak yerine düşürebilir.**
    

---

Hazır mıyız? Eğer istersen bu bilgileri uygulamalı bir örnekte birlikte deneyebiliriz. Bir “veri filtreleme” veya “form işleme” gibi küçük senaryo kurup baştan sona birlikte optimize edebiliriz 😎