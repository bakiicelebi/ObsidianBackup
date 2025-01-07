Elbette, bu sefer bir fırın kontrol sistemi yapalım. Fırın belirli bir süre boyunca pişirme yapacak, bu süre sonunda bir alarm çalacak ve fırın kapatılacak. Timer interrupt ile pişirme süresi ayarlanacak ve dış kesmeler ile pişirme başlatılıp durdurulacak.

### Senaryo
Bir fırın kontrol sistemi, belirli bir süre boyunca pişirme yapar. Pişirme süresi sonunda alarm çalar ve fırın kapanır. Sistemde pişirmeyi başlatmak ve durdurmak için iki buton bulunur.

#### Gereksinimler:
1. Pişirme başlatma butonu (INT0).
2. Pişirme durdurma butonu (INT1).
3. Pişirme süresi dolduğunda alarm çalar (P1.3).
4. Timer interrupt ile pişirme süresi kontrol edilir.
5. Pişirme süresi sırasında fırın (P1.0) çalışır.

### Çözüm

#### Donanım Yapılandırması:
- Pişirme başlatma butonu: `INT0`
- Pişirme durdurma butonu: `INT1`
- Fırın kontrol pini: `P1.0`
- Alarm pini: `P1.3`

#### Assembly Programı:

```assembly
; Fırın Kontrol Sistemi

            ORG     0000H
            SJMP    BASLA

            ORG     0003H   ; INT0 kesmesi (Pişirme başlat)
            LJMP    PISIRME_BASLAT_KESMESI

            ORG     000BH   ; T0 kesmesi (Pişirme süresi kontrolü)
            LJMP    TMR0KESMESI

            ORG     0013H   ; INT1 kesmesi (Pişirme durdur)
            LJMP    PISIRME_DURDUR_KESMESI

BASLA: 
            CLR     P1.0    ; Fırın başlangıçta kapalı
            CLR     P1.3    ; Alarm başlangıçta kapalı
            MOV     IE, #85H; Kesme yetkilendirme (INT0, INT1 ve Timer0)
            MOV     TMOD, #01H; Timer0 mod1
            MOV     TH0, #0F0H ; 1 saniye için yükleme değeri (yaklaşık)
            MOV     TL0, #0F0H
            CLR     TF0
            SETB    IT0
            SETB    IT1
            SJMP    $       ; Sonsuz döngü

TMR0KESMESI:
            CLR     TF0
            DJNZ    R0, TMR0KESMESI_END ; Pişirme süresini azalt
            CLR     P1.0    ; Fırını kapat
            SETB    P1.3    ; Alarmı aç
TMR0KESMESI_END:
            RETI

PISIRME_BASLAT_KESMESI:
            MOV     R0, #60 ; Pişirme süresi (60 saniye)
            CLR     P1.3    ; Alarmı kapat
            SETB    P1.0    ; Fırını aç
            MOV     TH0, #0F0H
            MOV     TL0, #0F0H
            SETB    TR0     ; Timer0'ı başlat
            RETI

PISIRME_DURDUR_KESMESI:
            CLR     TR0     ; Timer0'ı durdur
            CLR     P1.0    ; Fırını kapat
            CLR     P1.3    ; Alarmı kapat
            RETI

            END
```

#### Açıklamalar:
1. **TMR0KESMESI:** Timer0 interrupt rutini, belirli bir süre geçtiğinde tetiklenir ve pişirme süresini kontrol eder. Pişirme süresi dolduğunda fırını kapatır ve alarmı açar.
2. **PISIRME_BASLAT_KESMESI:** Pişirme başlatma butonuna basıldığında tetiklenir ve pişirme süresini başlatır. Fırını açar ve Timer0'ı başlatır.
3. **PISIRME_DURDUR_KESMESI:** Pişirme durdurma butonuna basıldığında tetiklenir ve pişirme süresini durdurur. Fırını ve alarmı kapatır.
4. **BASLA:** Başlangıçta gerekli ayarlamaları yapar. Timer'ı başlatır ve interrupt'ları etkinleştirir.

### Notlar
- Timer ayarları ve interrupt yönetimi, kullanılan mikrodenetleyiciye bağlı olarak değişebilir. Yukarıdaki örnek genel bir yaklaşımdır ve spesifik bir mikrodenetleyici için özelleştirilmelidir.
- Pişirme süresi ve alarm kontrolü, kullanılan donanım yapılandırmasına bağlı olarak değişebilir.

Bu örneği kendi mikrodenetleyicinizin talimat setine ve donanım yapılandırmasına uyacak şekilde uyarlayabilirsiniz. Başarılar!