Router yapısını bu şekilde yapabilir misin?  
  
/ (Operator or admin)  
/operator/group-matrix (gruplar)  
  
/operator/auth/login/:variant/?groupType=?groupId=  
  
Example:  
/operator/auth/login/clycle-based/?groupId=1234567 (optional groupName query param for excaping from extra request)  
  
/operator/auth/login/vehicle-based/?groupType="henkaten"/"repair"  
  
/operator/measurement/clycle-based/:groupId/ (Operator Ölçüm ekranı. Tanımlanan gruplar için)  
  
Example:  
/operator/measurement/clycle-based/231242  
/operator/measurement/clycle-based/324235  
  
/operator/measurement/vehicle-based/:groupType/ (Operator Ölçüm ekranı. static gruplar için)  
  
Example:  
/operator/measurement/vehicle-based/henkaten  
/operator/measurement/vehicle-based/repair





ÖlçümİçinGerekliBilgilerinTutulduğuContext  
Bir de mobilde toplu kayıt özelliği olacağından sequence başlatıldıktan sonra yapılan ölçümleri olacağı bir context de olacak gibi düşünebilirsin. Bu dediğinden kastın check item'ın contexti ise bu measureların bulunduğu contextin altında bir katman olmalı. Orada de measureları bu şekilde tutabilirsinsin.  
[{checkItemId:1, cycle:1,measurements:[23,22,64,33],vehicleId(assy yada body no değil. aratınca karşılık gelen id):1234,defectDescription(optional):"description text"}]  
  
Yada repair henkaten için bu şekilde  
[{checkItemId:1, measurements:[23,22,64,33],vehicleId(assy yada body no değil. aratınca karşılık gelen id):1234,defectDescription(optional):"description text"}]  
  
Bu arada bu cyclebased yada vehicle-based (repair/henkaten) için user sayfaları oluşturuken ayrı componentler olarak yapabiliriz. Ama içerdikleri alt componentler genelde ortak olacak. bu measure kısmı filan gibi. vehicle based ve vehicle based logicini tek componentde yaparsak kod karışabilir. Ondan ayrı yapıp oluşturduğumuz componentleri birleştirerek oluşturmak daha temiz olacal gibi



/Group1/CycleBased //1.Seçim tarafı  
/Group2/Henkaten-Repair //2.Seçim tarafı  
haslında henklaten repair'İn kullanıcı bazlı tanımı yok. ondan başta group1, 2 diye idyi belirmeye gerek olmuyor  
  
/operator/measurement/clycle-based/:groupId/ (Operator Ölçüm ekranı. Tanımlanan gruplar için)  
  
Example:  
/operator/measurement/clycle-based/231242  
/operator/measurement/clycle-based/324235  
  
/operator/measurement/vehicle-based/:groupType/ (Operator Ölçüm ekranı. static gruplar için)  
  
Example:  
/operator/measurement/vehicle-based/henkaten  
/operator/measurement/vehicle-based/repair  
  
Ondan group id sadece cycle based yani kullanıcı tarafından tanımlana gruplarda olacak. Vehicle based olanlar ayrı geliyor. Mesela cycle basedde o gruba atanmış itemler sequence başlatılmadan önce seçenekler olarak gelecekken, vehicle based olanlarda tüm tanımlı değerler gelecek