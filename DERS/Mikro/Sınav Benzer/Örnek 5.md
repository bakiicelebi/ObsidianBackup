Elbette, bu sefer bir akıllı ev sistemi yapalım. Bu sistem evdeki ışıkları, klima ve güvenlik alarmını kontrol eder. Sistemde çeşitli butonlar ve sensörler kullanılarak, farklı senaryolar gerçekleştirilir.

### Senaryo
Bir akıllı ev sistemi, evdeki ışıkları, klimayı ve güvenlik alarmını kontrol eder. Her bir cihaz için butonlar ve sensörler bulunur. Kullanıcı butonlara basarak cihazları kontrol edebilir ve sensörler belirli koşullarda otomatik işlem başlatır.

#### Gereksinimler:
1. Işıkları açma/kapama butonu (INT0).
2. Klima açma/kapama butonu (INT1).
3. Güvenlik alarmı sensörü (INT2).
4. Işıklar kontrol pini (P1.0).
5. Klima kontrol pini (P1.1).
6. Güvenlik alarmı pini (P1.2).
7. Zamanlayıcı ile belirli aralıklarla kontrol.

### Çözüm

#### Donanım Yapılandırması:
- Işıkları açma/kapama butonu: `INT0`
- Klima açma/kapama butonu: `INT1`
- Güvenlik alarmı sensörü: `INT2`
- Işıklar kontrol pini: `P1.0`
- Klima kontrol pini: `P1.1`
- Güvenlik alarmı pini: `P1.2`
- Timer kontrol pini: `P1.3`

#### Assembly Programı:

```assembly
; Akıllı Ev Sistemi

            ORG     0000H
            SJMP    BASLA

            ORG     0003H   ; INT0 kesmesi (Işıklar kontrolü)
            LJMP    ISIK_KESMESI

            ORG     000BH   ; T0 kesmesi (Zamanlayıcı kontrolü)
            LJMP    TMR0KESMESI

            ORG     0013H   ; INT1 kesmesi (Klima kontrolü)
            LJMP    KLIMA_KESMESI

            ORG     001BH   ; INT2 kesmesi (Güvenlik alarmı)
            LJMP    ALARM_KESMESI

BASLA: 
            CLR     P1.0    ; Işıklar başlangıçta kapalı
            CLR     P1.1    ; Klima başlangıçta kapalı
            CLR     P1.2    ; Alarm başlangıçta kapalı
            MOV     IE, #8FH; Kesme yetkilendirme (INT0, INT1, INT2 ve Timer0)
            MOV     TMOD, #01H; Timer0 mod1
            MOV     TH0, #3CH ; Yaklaşık 1 saniye için yükleme değeri
            MOV     TL0, #0B0H
            SETB    TR0     ; Timer0'ı başlat
            SETB    IT0
            SETB    IT1
            SETB    IT2
            SJMP    $       ; Sonsuz döngü

TMR0KESMESI:
            CLR     TF0
            MOV     TH0, #3CH ; Yeniden yükleme değeri
            MOV     TL0, #0B0H
            ; Belirli aralıklarla kontrol işlemleri burada yapılabilir.
            ; Örneğin, otomatik ışık kontrolü veya klima sıcaklık kontrolü gibi.
            RETI

ISIK_KESMESI:
            CPL     P1.0    ; Işıkların durumunu değiştir
            RETI

KLIMA_KESMESI:
            CPL     P1.1    ; Klimanın durumunu değiştir
            RETI

ALARM_KESMESI:
            SETB    P1.2    ; Alarmı aç
            ; Belirli bir süre sonra alarmı kapatmak için Timer0 kullanılabilir.
            MOV     TH0, #0FFH ; Alarm süresi için yükleme değeri
            MOV     TL0, #0FFH
            SETB    TR0     ; Timer0'ı başlat
            RETI

            END
```

#### Açıklamalar:
1. **TMR0KESMESI:** Timer0 interrupt rutini, belirli bir süre geçtiğinde tetiklenir ve evin kontrol işlemlerini yapar. Örneğin, otomatik ışık veya klima kontrolü.
2. **ISIK_KESMESI:** Işık butonuna basıldığında tetiklenir ve ışıkların durumunu değiştirir (aç/kapa).
3. **KLIMA_KESMESI:** Klima butonuna basıldığında tetiklenir ve klimanın durumunu değiştirir (aç/kapa).
4. **ALARM_KESMESI:** Güvenlik alarmı sensörü tetiklendiğinde alarmı açar ve Timer0'ı alarm süresi için başlatır.
5. **BASLA:** Başlangıçta gerekli ayarlamaları yapar. Timer'ı başlatır ve interrupt'ları etkinleştirir.

### Notlar
- Timer ayarları ve interrupt yönetimi, kullanılan mikrodenetleyiciye bağlı olarak değişebilir. Yukarıdaki örnek genel bir yaklaşımdır ve spesifik bir mikrodenetleyici için özelleştirilmelidir.
- Işık, klima ve alarm kontrolü, kullanılan donanım yapılandırmasına bağlı olarak değişebilir.

Bu örneği kendi mikrodenetleyicinizin talimat setine ve donanım yapılandırmasına uyacak şekilde uyarlayabilirsiniz. Başarılar!