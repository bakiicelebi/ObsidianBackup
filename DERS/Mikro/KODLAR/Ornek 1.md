``` assembly
ORG 0H
 
 SJMP BASLA
 ORG 30H
	 
BASLA: MOV P1,#0FFH
 ;P1’i giris kur
 CLR A
 MOV P2,A
 
YUKARI: JB P1.0,ASAGI 
 ;Yukari butonu
 
YUKARI2:JNB P1.0,YUKARI2
 CJNE A,#9,ARTTIR
 MOV A,#0
 MOV P2,A
 SJMP ASAGI
 
ARTTIR: INC A
MOV P2,A

ASAGI: JB P1.1,YUKARI 
 ;Asagi butonu
 
ASAGI2: JNB P1.1,ASAGI2
CJNE A,#0,AZALT
MOV A,#9
MOV P2,A
 SJMP YUKARI
 
 
 AZALT: DEC A
MOV P2,A
SJMP YUKARI
END
```