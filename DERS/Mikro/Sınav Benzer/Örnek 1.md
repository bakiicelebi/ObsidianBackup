Elbette, benzer bir örnek daha türetelim. Bu sefer bir kapı güvenlik sistemi yapalım. Kapı açıldığında bir alarm devreye girer ve kapı kapatıldığında alarm kapanır. Ayrıca, bir "kapı açıldı" ve "kapı kapandı" sinyalleri olacak.

### Senaryo
Bir kapı güvenlik sistemi, kapı açıldığında alarmı aktif hale getirir ve kapı kapandığında alarmı devre dışı bırakır. Sistem ayrıca kapının açıldığını ve kapandığını belirten sinyalleri yönetir. Alarmın yanıp sönmesi için bir LED kullanılır.

#### Gereksinimler:
1. Kapı açıldığında alarm devreye girer ve LED yanıp söner.
2. Kapı kapandığında alarm kapanır ve LED söner.
3. Kapının açıldığını ve kapandığını gösteren sinyaller.
4. Timer interrupt kullanarak alarm LED'ini kontrol edin.

### Çözüm

#### Donanım Yapılandırması:
- Alarm kontrol pini: `P1.0`
- LED çıkış pini: `P1.3`
- Kapı açıldı sinyali: `INT0`
- Kapı kapandı sinyali: `INT1`


#### Assembly Programı:

```assembly
; Kapı Güvenlik Sistemi

ORG 0000H
    SJMP MAIN

ORG 0003H
    LJMP INT0_ISR  ; Kapi açildiginda kesme yönlendirme

ORG 0013H
    LJMP INT1_ISR  ; Kapi kapandiginda kesme yönlendirme

ORG 000BH
    LJMP TIMER_ISR ; Timer kesmesi yönlendirme


ORG 30H
MAIN:
    MOV P1, #00H   ; P1 portunu temizle (Alarm ve LED kapali)
    MOV TMOD, #01H ; Timer 0 mod 1 (16-bit timer)
    MOV IE, #85H   ; EX0, EX1 ve ET0 kesmeleri etkinlestir
    SETB IT0
	SETB IT1
    SETB EA        ; Genel kesme etkinlestir
    SJMP $         ; Sürekli döngü

; INT0 ISR - Kapi Açildi
INT0_ISR:
    SETB P1.0      ; Alarmi aktif et (P1.0)
    SETB TR0       ; Timer0'i baslat
    RETI

; INT1 ISR - Kapi Kapandi
INT1_ISR:
    CLR P1.0       ; Alarmi devre disi birak (P1.0)
    CLR TR0        ; Timer0'i durdur
    CLR P1.3       ; LED'i söndür (P1.3)
    RETI

; Timer ISR - LED Yanip Sönme
TIMER_ISR:
    CLR TF0
    SETB P1.3       ; LED'i degistir (P1.3)
    MOV TH0, #0D8H ; Timer'i yeniden yükle (yüksek byte)
    MOV TL0, #0F0H ; Timer'i yeniden yükle (düsük byte)
    RETI

END
```


