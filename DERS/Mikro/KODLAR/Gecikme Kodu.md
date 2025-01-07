GECIKME:MOV R0,#255
MOV R1,#255
BEKLE:DJNZ R0,BEKLE ;R0'ı 1 azalt '0' değilse Bekle'ye dallan
MOV R0,#255 
DJNZ R1,BEKLE ;R1'i 1 azalt '0' değilse Bekle'ye dallan 
RET ;alt programdan dön 