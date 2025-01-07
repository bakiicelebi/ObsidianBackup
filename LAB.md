
bekle:
				mov r7 , #0ffh
				tekrar:
				djnz r6,$
					djnz r7, tekrar
					ret
					
					
					end



ORG 00h


START:
    MOV P0, #0FFh 
    MOV P2, #003h  
    
LOOP:
    JB P0.0, $
	MOV A,P2;
    CPL A ;
	MOV P2,A;
    JNB P0.0, $
    SJMP LOOP   
    
END                      








ORG 00h


START:
	;P0 Porut
	MOV P0, #0FEH
	acall bekle
	MOV P0, #0FCH
	acall bekle
	MOV P0, #0F8H
	acall bekle
	MOV P0, #0F0H
	acall bekle
	MOV P0, #0E0H
	acall bekle
	MOV P0, #0C0H
	acall bekle
	MOV P0, #080H
	acall bekle
	MOV P0, #000H
	acall bekle
	
	; P1 PORTU
	CLR P1.7;
	acall bekle
	CLR P1.6
	acall bekle
	CLR P1.5
	acall bekle
	CLR P1.4
	acall bekle
	CLR P1.3
	acall bekle
	CLR P1.2
	acall bekle
	CLR P1.1
	acall bekle
	CLR P1.0
	acall bekle
	MOV P0, #0FFH
	acall bekle
	MOV P1, #0FFH
	acall bekle
	
	
	
	SJMP START;

bekle:
	mov r7 , #0ffh
		tekrar:
			djnz r6,$
				djnz r7, tekrar
				ret

	
END                      








ORG 00h

BASLA:
	ACALL Ayaz;
	acall bekle;
	acall bekle;
	acall bekle;
	acall bekle;
	ACALL Byaz;
	acall bekle;
	acall bekle;
	acall bekle;
	acall bekle;
	
	SJMP BASLA;

Ayaz:
	MOV P0,#01H
	MOV P1,#0EEH
	MOV P2,#0EEH
	MOV P3,#01H
	ret

Byaz:
	MOV P0,#00H
	MOV P1,#066H
	MOV P2,#066H
	MOV P3,#099H
	ret

bekle:
	mov r7 , #0ffh
		tekrar:
		mov r6,#0ffh
			djnz r6,$
				djnz r7, tekrar
				ret

	
END                      


ORG 00h

BASLA:
	ACALL Ayaz;
	acall bekle;
	acall bekle;
	acall bekle;
	acall bekle;
	ACALL Byaz;
	acall bekle;
	acall bekle;
	acall bekle;
	acall bekle;
	ACALL Uyaz;
	acall bekle;
	acall bekle;
	acall bekle;
	acall bekle;
	
	SJMP BASLA;

Ayaz:
	MOV P0,#01H
	MOV P1,#0EEH
	MOV P2,#0EEH
	MOV P3,#01H
	ret

Byaz:
	MOV P0,#00H
	MOV P1,#066H
	MOV P2,#066H
	MOV P3,#099H
	ret


Uyaz:
	MOV P0,#00H
	MOV P1,#07FH
	MOV P2,#07FH
	MOV P3,#00H
	ret
	
bekle:
	mov r7 , #0ffh
		tekrar:
		mov r6,#0ffh
			djnz r6,$
				djnz r7, tekrar
				ret

	
END                      
