; Otomat Sistemi

            ORG     0000H
            SJMP    BASLA

            ORG     0003H   ; INT0 kesmesi (Su)
            LJMP    SU_KESMESI

            ORG     000BH   ; T0 kesmesi (LED yanıp sönme)
            LJMP    TMR0KESMESI

            ORG     0013H   ; INT1 kesmesi (Soda)
            LJMP    SODA_KESMESI

            ORG     001BH   ; INT2 kesmesi (Kahve)
            LJMP    KAHVE_KESMESI

BASLA: 
            CLR     P1.0    ; LED su kapalı
            CLR     P1.1    ; LED soda kapalı
            CLR     P1.2    ; LED kahve kapalı
            MOV     IE, #95H; Kesme yetkilendirme (INT0, INT1, INT2 ve Timer0)
            MOV     TMOD, #02H; Timer0 mod2
            MOV     TH0, -250 ; 250 mikro sn
            MOV     TL0, -250
            CLR     TF0
            SETB    IT0
            SETB    IT1
            SETB    IT2
            SJMP    $       ; Sonsuz döngü

TMR0KESMESI:
            CLR     TF0
            CPL     P1.0    ; Su LED'i tersle (yanıp sönme)
            CPL     P1.1    ; Soda LED'i tersle (yanıp sönme)
            CPL     P1.2    ; Kahve LED'i tersle (yanıp sönme)
            RETI

SU_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.0    ; Su LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

SODA_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.1    ; Soda LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

KAHVE_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.2    ; Kahve LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

            END
