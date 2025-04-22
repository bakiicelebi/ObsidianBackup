Süper, o zaman hadi küçük bir senaryo oluşturalım:  
**Senaryo:**  
Bir kullanıcı listemiz var ve bu listeyi filtreleyip ekrana yazdırıyoruz.  
Ayrıca her kullanıcı için bir "Seç" butonu var.

Biz:

- `useMemo` ile filtre işlemini optimize edeceğiz.
    
- `useCallback` ile butonun fonksiyonunu hafızada tutacağız.
    
- `React.memo` ile kullanıcı bileşenini gereksiz render’lardan koruyacağız.
    

---

## 💻 Örnek: Kullanıcı Filtreleme Uygulaması

```tsx
import React, { useState, useMemo, useCallback } from "react";

// 🔹 Alt bileşeni memo ile sarmalıyoruz
const UserCard = React.memo(({ user, onSelect }) => {
  console.log("Render:", user.name);

  return (
    <div style={{ border: "1px solid gray", padding: "8px", margin: "8px" }}>
      <p>{user.name}</p>
      <button onClick={() => onSelect(user.id)}>Seç</button>
    </div>
  );
});

const App = () => {
  const [filter, setFilter] = useState("");
  const [selectedUserId, setSelectedUserId] = useState(null);

  const users = [
    { id: 1, name: "Ali" },
    { id: 2, name: "Ayşe" },
    { id: 3, name: "Mehmet" },
    { id: 4, name: "Zeynep" }
  ];

  // 🔹 Filtreleme işlemini useMemo ile yapıyoruz
  const filteredUsers = useMemo(() => {
    console.log("Filtreleme yapılıyor...");
    return users.filter(user =>
      user.name.toLowerCase().includes(filter.toLowerCase())
    );
  }, [users, filter]);

  // 🔹 Fonksiyonu useCallback ile sabit tutuyoruz
  const handleSelect = useCallback((id) => {
    setSelectedUserId(id);
  }, []);

  return (
    <div style={{ padding: "16px" }}>
      <h2>Kullanıcı Seç</h2>
      <input
        type="text"
        placeholder="Ara..."
        value={filter}
        onChange={(e) => setFilter(e.target.value)}
      />

      <p>Seçilen Kullanıcı ID: {selectedUserId ?? "Yok"}</p>

      <div>
        {filteredUsers.map((user) => (
          <UserCard key={user.id} user={user} onSelect={handleSelect} />
        ))}
      </div>
    </div>
  );
};

export default App;
```

---

### 🎯 Ne Gördük?

- 🔁 Sadece filter değişince `filteredUsers` yeniden hesaplanıyor (`useMemo`)
    
- 🧠 `handleSelect` her render’da yeniden oluşmuyor (`useCallback`)
    
- 🧍‍♂️ `UserCard` sadece props değişince render oluyor (`React.memo`)
    
- 🧪 Konsolda göreceğin "Render:" logları sayesinde gerçekten performans kazancı oluyor mu test edebilirsin.
    

---
