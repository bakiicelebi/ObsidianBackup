Service -> tum business lojik burada oluyor

Repository -> DB ile iletisim burada yapiliyor (sql sorgulari)

Controller -> Endpoint tanimlari ve disariyla iletisim

Entity -> DB tablolarina karsilik gelen objeler

DTO -> Data Transfer Object, adi ustunde veri transferinde kullanilan objeler bunlar da. Mesela fe ye id ve name alanini gondermek istiyorsun sadece ama enitity'de daha fazla alan var bunun icin sadece id ve name alani iceren bir dto olusturup onu controller dan return edersin.