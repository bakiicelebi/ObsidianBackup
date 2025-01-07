; Asansör Kontrol Sistemi

            ORG     0000H
            SJMP    BASLA

            ORG     0003H   ; INT0 kesmesi (Kat 1)
            LJMP    KAT1_KESMESI

            ORG     000BH   ; T0 kesmesi (Asansör hareket kontrolü)
            LJMP    TMR0KESMESI

            ORG     0013H   ; INT1 kesmesi (Kat 2)
            LJMP    KAT2_KESMESI

            ORG     001BH   ; INT2 kesmesi (Kat 3)
            LJMP    KAT3_KESMESI

BASLA: 
            CLR     P1.0    ; Kat 1 LED kapalı
            CLR     P1.1    ; Kat 2 LED kapalı
            CLR     P1.2    ; Kat 3 LED kapalı
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
            ; Asansörün hareketi burada kontrol edilir.
            ; Örneğin, bir motor kontrol sinyali gönderilebilir.
            RETI

KAT1_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.0    ; Kat 1 LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

KAT2_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.1    ; Kat 2 LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

KAT3_KESMESI:
            CLR     P1.0    ; Diğer LED'leri kapat
            CLR     P1.1
            CLR     P1.2
            SETB    P1.2    ; Kat 3 LED'i yanar
            SETB    TR0     ; Timer0'ı başlat
            RETI

            END
