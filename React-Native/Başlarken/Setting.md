**1. Yeni görev nesnesi oluşturun:**

JavaScript

```
const renderInput = () => {
  const newTask = {
    id: 1,
    title: "aca",
    author: "A",
    read: true,
  };

  setTasks([...tasks, newTask]);
};
```

Kodu dikkatli kullanın. [Daha fazla bilgi](https://bard.google.com/faq#coding)

content_copy

**2. Mevcut görevleri güncelleyin:**

Mevcut görevleri güncellemek istiyorsanız, `setTasks` fonksiyonunu bir callback fonksiyonuyla kullanabilirsiniz:

JavaScript

```
const renderInput = () => {
  setTasks((prevTasks) => {
    return prevTasks.map((task) => {
      if (task.id === 1) { // Güncellemek istediğiniz görevin ID'sini belirtin
        return {
          ...task,
          title: "aca",
          author: "A",
          read: true,
        };
      }

      return task;
    });
  });
};
```

Kodu dikkatli kullanın. [Daha fazla bilgi](https://bard.google.com/faq#coding)

content_copy

**Dikkat edilmesi gerekenler:**

- `setTasks` fonksiyonunu bir callback fonksiyonuyla kullandığınızda, React'in mevcut state'i güncellemesini ve bileşenleri yeniden render etmesini sağlarsınız.
- `id` özellikleri, görevlerin benzersiz bir şekilde tanımlanmasını sağlar.
- Veri tiplerinin uyumlu olduğundan emin olun.

**Eğer amacınız tüm görevleri temizlemekse, kodu şu şekilde değiştirebilirsiniz:**

JavaScript

```
const renderInput = () => setTasks([]);
```