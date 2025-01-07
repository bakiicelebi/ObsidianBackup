Mesela böyle bir endpoint olabilir check itemleri getirmek için.  
  
GET operator/group-check-items/:groupId?modelId=1234&processId=1234  
  
Response'u da böyle. Rank bilgisini de burada dönmem gerekecek  
{  
cycles: [{ checked: 4, total: 342 }, { checked: 0, total: 342 }],  
checkItems: [{ checkItemId: 1234, rank: "S", checkItemName: "FL RH Outdoor", isLoctite: true, isSensitive: false, status: "OK",cycle:2(sadece ilk 2 cycleda bu itemi gösterecen mesela) }]  
},  
  
 Sonra bir de check itemlerı daha detaylı çektiğın bin endpoint olacak check idsi ile, measurelerı target min max mı, yoksa ok ng olarak mı ölcülecek, tool bilgileri vs burada gelecek.  
  
Modeller şöyle gelebilir cycle bazılı. GET operator/models-by-group/:groupId  
[{  
modelId:123,  
modelCode:CHR  
}]  

Modeller şöyle gelebilir vehicle bazlı ekranlarda(henkaten repair). GET operator/models-by-department/:departmentId  
[{  
modelId:123,  
modelCode:CHR  
}]

Processler  deşöyle gelebilir cycle bazılı(Kullanıcının tanımladığı grup ekranları için). GET operator/process-by-group/:groupId  
[{  
processId:123,  
processCode:TRIM1  
}]  
  
Processler şöyle gelebilir vehicle bazlı ekranlarda(henkaten repair). GET operator/process-by-department/:departmentId  
[{  
processId:123,  
processCode:TRIM1  
}]


const requestBody = {

                username: username,

                password: password,

                productionDay: 27,

                productionMonth: 7,

                productionYear: 2024,

                shiftId: 19,

                groupId: 1,

                henkatenId: 52359,

            };

