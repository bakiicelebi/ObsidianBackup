 - [x] Login ekranına grubun önüne departman bilgisi eklenmelidir.

- [x] login sonrası açılan ekranda Süreç seçin yerine TR için Proses seçin olmalıdır

- [x] headerde kullanıcı adının yanında sicil numarası da yazmalıdır. 99469-Hale Mammadova(QA/MQEA) gibi

- [x] PWT grubunda tool kısmında fazladan boşluk kalmıştır

- [x] sağ tarafta çıkan QI bilgisi (WAU-465) QI açıklaması şeklinde olmalıdır. Bu bilgiler şuan düzgün gelmiyor. Bununla beraber kalite ekipman bilgileri de dogru gelmiyor

- [x] maddeler arasında geçiş yapıldığında sag tarafta bilgiler senkron akmıyor. madde ismi yanlış geliyor

- [x] Olcum resimleri gorunmuyor, Aynı zamanda acıklamaları da.

- [x] Şifre değiştirme hata aldı

- [x] TMMT’de sadece GVIS numarası mevcut, TIS gelmesine gerek yok

- [x] Ozellikler kısmı da boşsa goruntumesine gerek yok

- [x] Arac bulunamadığı durumda 2 tane aynı uyarıdan çıkıyor. 2. olarak çıkan Arac bulunamadı uyarısı kaldırılmalıdır

- [ ] BT error hatalarında başlıklardan sonra : eklenmelidir. Çıkan aşağıdaki uyarı net değil

- [ ] guncelleme esnasında bağlantı gitti, ama onceden guncelleme yapılmıştıu. Veriyi kaydet butonu buna ragmen disable kaldı. Guncelleme esnasında manual olarak bile guncelleme yapıldıgında veriyi kaydet butonu aktifleşmedi

- [x] Kalite Ekipmanı yerine Kalite Kontrol ARacı yazmalıdır. UK için de **Quality Check Tool** olmalıdır

- [x] Soket yerine Soket Boyutu olmalıdır UK için Socket Size.

- [x] Olcum resmi yanında label kaldırılmalıdır zaten başlık var.

- [x] Süre iconu yanındaki Süre label kaldırılmalıdır. sadece 60 sn yazması yeterlidir. Şuan ayrıca s yazmaktadır. Dakika olursa dk. olmalıdır.

- [x] Kontrolu başlatma ekranında headerda Proses ismi yanında DEP bilgisi gelmemiştir.

- [x] Geri butonu uppercase olmalıdır. GERİ gibi. UK için BACK

- [x] Kontrolu başlat ekranında maddelerin yanında sıra numarası gelmemiştir. 

- [x] Olcum değerlerinde . sonrası 3 rakam varsa yuvarlanarak gösterilmelidir.

- [x] Henkaten ve repair dışında arama tipi inputu altına **30 Nm'nin altındaki torklar, 0,5 Nm aralıklarla ifade edilir.** yazılmalıdır. UK için Torques below 30 Nm are expressed in increments of 0.5 Nm.

- [x] Feedback F.B. gibi değil FB. olarak gösterilebilir.

- [x]  cycle altındaki tüm maddeler tamamlanmış olmasına rağmen diğer cycle’a geçiş yapmadı.

- [x] departmanın grubu yoksa iş listesinde gösterme

A) Eğer aktif cycle içinde ölçüm yapılacak herhangi bir madde yoksa bu durumda “**Active** **Cycle tamamlandı**” uyarısı çıkar ve kullanıcı mesajı kapatınca bir sonraki cycle başlar.

B)Eğer bitmemiş cycle’lar varsa bu durumda otomatik olarak o cycle’a geçiş yapılır ve kontrol edilmemiş ilk madde seçili gelerek ekran yüklenir.

C)Eğer tüm cycle’lar başarılı bir şekilde tamamlanmış ise bu durumda “**Tüm cycle’lar tamamlandı**” uyarısı çıkar.

_Eğer tool seçimi yapılarak ölçümler giriliyorsa bu durumda aşağıdaki kontroller yapılır:_

C) Seçili tool içindeki maddeler tamamlanana kadar ölçümler sırasıyla yapılır. Tool içindeki kontroller tamamlandıktan sonra uyarı çıkar ve kullanıcının yeni bir tool seçimi ile ilerlemesi gerektiği bildirilir.

Bu durumda cycle bilgisi yeniden yüklenir ve tool seçimi de ALL olarak gösterilir. Kullanıcı bu listeden tekrar tool seçimi yaparak aynı şekilde ilerleyebilir. Eğer aktif cycle’ın altındaki iş listesinin hepsi tamamlanmış ise bu durumda bu uyarı mesajı yerine “**Active Cycle Tamamlandı**” uyarısı çıkar ve yeni cycle’a geçiş yapılır.

D) Eğer tüm cycle’lar başarılı bir şekilde tamamlanmış ise bu durumda “**Tüm cycle’lar tamamlandı**” uyarısı çıkar.