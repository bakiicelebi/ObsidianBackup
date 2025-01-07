**Employee** entity'si diğer entity'lerle ilişkili olduğu için **Navigation Properties** eklenmesi gerekiyor. Örneğin, **Employee** bir veya daha fazla randevuya (Appointment) ve çalıştığı salona (Salon) bağlı olabilir. Bu nedenle, bu ilişkiler için aşağıdaki düzenlemeleri yapıyoruz.

### Güncel Employee Entity (Navigation Property Eklendi)

```csharp
public class Employee
{
    [Key]
    public int EmployeeId { get; set; }

    [Required]
    [MaxLength(100)]
    public string Name { get; set; }

    [Required]
    [MaxLength(50)]
    public string Username { get; set; }

    [Required]
    [MaxLength(255)]
    public string Password { get; set; }

    [Required]
    [MaxLength(100)]
    public string Position { get; set; }

    [DataType(DataType.Currency)]
    public decimal Salary { get; set; }

    [Required]
    [MaxLength(15)]
    public string Phone { get; set; }

    [Required]
    [EmailAddress]
    public string Email { get; set; }

    public DateTime HireDate { get; set; } = DateTime.Now;

    [Required]
    public AuthLevel AuthLevel { get; set; }

    [MaxLength(200)]
    public string Address { get; set; }

    [MaxLength(500)]
    public string ProfileImageUrl { get; set; }

    public bool IsActive { get; set; } = true;

    [MaxLength(1000)]
    public string WorkHours { get; set; }

    // Navigation Properties
    public int SalonId { get; set; } // Foreign Key
    public Salon Salon { get; set; } // Bir çalışanın bağlı olduğu salon

    public ICollection<Appointment> Appointments { get; set; } // Çalışanın randevuları
}
```

---

### Diğer Entity'ler

#### 1. **Customer (Müşteri) Entity**

```csharp
public class Customer
{
    [Key]
    public int CustomerId { get; set; }

    [Required]
    [MaxLength(100)]
    public string Name { get; set; }

    [Required]
    [MaxLength(50)]
    public string Username { get; set; }

    [Required]
    [MaxLength(255)]
    public string Password { get; set; }

    [Required]
    [MaxLength(15)]
    public string Phone { get; set; }

    [Required]
    [EmailAddress]
    public string Email { get; set; }

    [MaxLength(500)]
    public string ProfileImageUrl { get; set; } // Profil resmi

    public ICollection<Appointment> Appointments { get; set; } // Müşterinin randevuları
}
```

---

#### 2. **Service (Hizmet) Entity**

```csharp
public class Service
{
    [Key]
    public int ServiceId { get; set; }

    [Required]
    [MaxLength(150)]
    public string Name { get; set; }

    [Required]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }

    [Required]
    public TimeSpan Duration { get; set; } // Hizmet süresi

    public int SalonId { get; set; } // Foreign Key
    public Salon Salon { get; set; } // Hizmeti sunan salon

    public ICollection<Appointment> Appointments { get; set; } // Hizmetle ilişkilendirilmiş randevular
}
```

---

#### 3. **Salon (Salon) Entity**

```csharp
public class Salon
{
    [Key]
    public int SalonId { get; set; }

    [Required]
    [MaxLength(150)]
    public string Name { get; set; }

    [Required]
    [MaxLength(200)]
    public string Address { get; set; }

    [Required]
    [MaxLength(20)]
    public string Phone { get; set; }

    [MaxLength(500)]
    public string LogoUrl { get; set; } // Salon logosu

    [Required]
    public string OpeningHours { get; set; } // Çalışma saatleri JSON formatı olabilir

    public ICollection<Employee> Employees { get; set; } // Salonun çalışanları
    public ICollection<Service> Services { get; set; } // Salonun sunduğu hizmetler
}
```

---

#### 4. **Appointment (Randevu) Entity**

```csharp
public class Appointment
{
    [Key]
    public int AppointmentId { get; set; }

    [Required]
    public int EmployeeId { get; set; } // Foreign Key
    public Employee Employee { get; set; } // Randevuyu alan çalışan

    [Required]
    public int CustomerId { get; set; } // Foreign Key
    public Customer Customer { get; set; } // Randevuyu alan müşteri

    [Required]
    public int ServiceId { get; set; } // Foreign Key
    public Service Service { get; set; } // Alınan hizmet

    [Required]
    public DateTime AppointmentTime { get; set; } // Randevu zamanı

    [MaxLength(500)]
    public string Notes { get; set; } // Ek notlar

    public decimal TotalPrice { get; set; } // Toplam ücret

    public bool IsConfirmed { get; set; } = false; // Randevu onay durumu
}
```

---

### Sonraki Adımlar

- **Tablo İlişkileri**: Tüm entity'ler birbiriyle doğru şekilde ilişkilendirildi. Bu yapıya dayanarak Entity Framework Core kullanarak veritabanınızı kolayca oluşturabilirsiniz.
- **Migration ve Veri Tabanı Güncellemesi**:
    
    ```bash
    dotnet ef migrations add InitialMigration
    dotnet ef database update
    ```
    

Eğer başka tablolar ya da özel durumlar (örneğin, kullanıcı yetkilendirme) eklemek istiyorsanız, detayları konuşabiliriz. 😊