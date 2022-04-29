# Hayvanat Bahçesi Yönetimi
````
1. Hayvanlar:
2. Atlar (atlar, zebralar, eşekler vb.),
3. Kedigiller (kaplanlar, aslanlar vb.),
4. Kemirgenler (sıçanlar, kunduzlar vb.) gibi gruplardaki türlerle karakterize edilir.
5. Hayvanlar hakkında depolanan bilgilerin çoğu tüm gruplamalar için aynıdır.
tür adı, ağırlığı, yaşı vb.
6. Sistem ayrıca her hayvan için belirli ilaçların dozajını alabilmeli => getDosage ()
7. Sistem Yem verme zamanlarını hesaplayabilmelidir => getFeedSchedule ()
````
Sistemin bu işlevleri yerine getirme mantığı, her gruplama için farklı olacaktır. Örneğin, atlar için yem verme algoritması farklı olup, kaplanlar için farklı olacaktır.

Polimorfizm modelini kullanarak, yukarıda açıklanan durumu ele almak için bir sınıf diyagramı tasarlayın.

## Class Diyagramı
![HayvanatBahcesiYonetimi](https://user-images.githubusercontent.com/75527964/165880166-6427d0ae-01dc-4181-9bf9-12d69b485e5c.png)

