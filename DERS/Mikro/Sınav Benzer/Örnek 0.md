### Senaryo

Bir fabrikada bir üretim hattı kontrol sistemi tasarlıyorsunuz. Bu sistemde, üretim hattının düzgün çalıştığını göstermek için her saniye bir LED yanıp sönüyor ve her saniye bir seri port üzerinden merkezi kontrol birimine 'A' karakteri gönderiliyor. Bu merkezi kontrol birimi, üretim hattının çalışmasını izliyor ve gerektiğinde müdahale ediyor. LED'in yanıp sönmesi, operatörlere üretim hattının çalıştığını görsel olarak gösterirken, seri port üzerinden gönderilen 'A' karakteri, merkezi kontrol biriminin üretim hattının durumunu dijital olarak izlemesini sağlıyor.

### Assembly Kodu


```assembly
ORG 0000H           ; Başlangıç adresi
    SJMP START      ; Programın başlangıcına atla

ORG 000BH           ; Timer 0 Interrupt Vektör Adresi
    AJMP TIMER0_ISR ; Timer 0 kesintisi meydana geldiğinde ISR'ye atla

START:
    ; Timer 0 Ayarları
    MOV TMOD, #01H  ; Timer 0'ı Mod 1 (16-bit Timer) olarak ayarla
    MOV TH0, #0x3C  ; Timer yüksek baytını yükle (1 saniye için)
    MOV TL0, #0xB0  ; Timer düşük baytını yükle (1 saniye için)
    SETB TR0        ; Timer 0'ı başlat
    SETB ET0        ; Timer 0 kesintilerini etkinleştir
    SETB EA         ; Tüm kesintileri etkinleştir

    ; Seri Port Ayarları
    MOV SCON, #50H  ; Seri portu Mod 1 (8-bit UART) olarak ayarla, REN=1
    MOV TMOD, #20H  ; Timer 1'i Mod 2 (8-bit Auto-Reload) olarak ayarla
    MOV TH1, #0FDH  ; Baud rate için Timer 1 reload değeri (9600 baud)
    SETB TR1        ; Timer 1'i başlat

MAIN_LOOP:
    SJMP MAIN_LOOP  ; Ana döngü, burada bekleme yapılıyor

TIMER0_ISR:
    CLR TR0         ; Timer 0'ı durdur
    MOV TH0, #0x3C  ; Timer yüksek baytını tekrar yükle
    MOV TL0, #0xB0  ; Timer düşük baytını tekrar yükle
    SETB TR0        ; Timer 0'ı tekrar başlat

    CPL P1.0        ; P1.0 pinini tersle (LED'i yak/söndür)
    
    MOV SBUF, #'A'  ; Seri port üzerinden 'A' karakterini gönder
WAIT_FOR_TX:
    JNB TI, WAIT_FOR_TX ; TI bayrağı set olana kadar bekle
    CLR TI          ; TI bayrağını temizle

    RETI            ; Kesintiden çık

END
```

### Detaylı Açıklamalar
1. **Başlangıç Ayarları:**
   - Programın başında, `ORG 0000H` komutu ile program başlangıç adresi belirtilir ve `SJMP START` komutu ile başlangıç adresine atlanır.
   - `ORG 000BH`, Timer 0 kesintisi için kesme vektör adresini ayarlar ve `AJMP TIMER0_ISR` komutu ile kesinti meydana geldiğinde ISR'ye atlar.

2. **Timer 0 Ayarları:**
   - `TMOD` register'ı, Timer 0'ı Mod 1 (16-bit Timer) olarak ayarlar.
   - `TH0` ve `TL0` register'ları, Timer 0'ı 1 saniyelik bir periyot için başlangıç değerleri ile yükler.
   - `TR0` komutu, Timer 0'ı başlatır.
   - `ET0` komutu, Timer 0 kesintilerini etkinleştirir.
   - `EA` komutu, global kesintileri etkinleştirir.

3. **Seri Port Ayarları:**
   - `SCON` register'ı, Seri portu Mod 1 (8-bit UART) olarak ayarlar ve veri alımını etkinleştirir (REN=1).
   - `TMOD` register'ı, Timer 1'i Mod 2 (8-bit Auto-Reload) olarak ayarlar.
   - `TH1`, Timer 1 için 9600 baud rate'ini ayarlamak için kullanılır.
   - `TR1`, Timer 1'i başlatır.

4. **Ana Döngü:**
   - `MAIN_LOOP`, programın sonsuz döngüsüdür ve burada bekleme durumu yaratılır.

5. **Timer 0 ISR:**
   - Timer 0 kesintisi meydana geldiğinde ISR çalışır.
   - `TR0` komutu ile Timer 0 durdurulur ve `TH0` ile `TL0` register'ları yeniden yüklenir.
   - `TR0` komutu ile Timer 0 tekrar başlatılır.
   - `CPL P1.0` komutu ile P1.0 pinindeki LED terslenir (yakılır veya söndürülür).
   - `SBUF` register'ına 'A' karakteri yüklenir ve seri port üzerinden gönderilir.
   - `WAIT_FOR_TX` etiketi ile `TI` bayrağı set olana kadar beklenir ve `CLR TI` komutu ile `TI` bayrağı temizlenir.
   - `RETI` komutu ile ISR'den çıkılır.

Bu senaryo, her saniye bir LED'in yanıp sönmesini ve seri port üzerinden bir karakter gönderilmesini içerir. Bu, üretim hattının durumu hakkında görsel ve dijital geri bildirim sağlar.