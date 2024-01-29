# Otel Otomasyon Taslağı

## Genel Amaç ve Yapılacaklar
- Bir otelde bulunan tüm odaların akıllı hale getirilerek sistemlerin otonom beceri kazanmalarını sağlamak.
- Otelde bulunan çalışanların bu sisteme entegre bir biçimde çalışmalarını sağlayabilecek sistemlerin tasarlanması.
- Daha önceden otelde bulunan sistemlere entegre bir biçimde çalışabilmesi.
- Odalarda bulunan lamba, klima, priz, perde gibi yapıların sisteme uygun hale getirilmesi.
- Otel içinde bulunan klimaların veya benzeri sistemlerin sisteme entegre şekilde otonom hale getirilmesi.
- KNX, RS485, BACnet gibi uyumlu cihazların sisteme entegre şekilde çalışmalarının sağlanması.
- Otel içinde bulunan televizyon, çalışan tabletleri gibi farklı cihazların sisteme entegre şekilde çalışabilmeleri.
- Tüm bu sistemlerin izlenebilmesi için web arayüzü üzerinden izleme sistemlerinin tasarlanması.
- Otel odalarında bulunan farklı senaryolara uygun şekilde çalışabilmesi için config sisteminin tasarlanması. KNX uyumlu cihazlar gibi sistemlere uygun şekilde çalışmalarının sağlanması.
- Otel ağ yapılandırmalarının yapılması.
- Tek bir sistem üzerinden hem çalışanların yönetilebilmesi hem de üretilen verinin kontrolü.
- Sistemin geliştirilebilir bir yapı üzerine oturtulması ve üretilen her kodun dökümantasyonunun yapılması.
- Config yapısının çok modüler bir şekilde inşa edilmesi.
- KNX gibi cihazlar için ETS yazılımının ürettiği veritabanı kullanılarak, ETS yazılımını doğrudan kullanmadan çalışabilecek bir sistemin tasarlanması.
- Config tasarımının detaylı ve kolay bir şekilde yapılandırılması, üretilen configlerin kolay bir şekilde STM32 içinde çalışabilmesi sağlanacak. Web arayüzünden config tasarımı yapılacak ve bu STM32 içinde doğrudan çalışabilecek.

## Sisteme Genel Bakış
Otelimizin her odasının yapısının farklı olduğunu düşünelim. Her odada KNX uyumlu, RS485 uyumlu cihazlarımız var. Varlık sensörleri, lamba, klima gibi farklı yapılarımız mevcut. Böyle bir otelde her odaya uygun şekilde çalışabilecek odaların kontrollerini sağlamak en genel amacımızdır. Bir örnek vermek gerekirse:
- Bir müşteri odadan çıktıktan sonra lambaları otomatik kapatacak. Klimayı otomatik kapatacak bir sistem istiyorsunuz. Müşteri odadan çıkmadan önce telefonunda odanın temizlenmesini isteyebilmeli ve müşteri odadan çıktıktan sonra bu işle ilgilenen personele otomatik bir bildirim gitmeli.
- Müşteri telefonunda odadaki herhangi bir lambayı veya klimanın ayarını değiştirebilmeli. Tüm bunları ve daha fazlasını yapabilecek bir sistem.
- Otel

in içerisindeki enerji verimliliğini takip ederek gelecekte daha yaşanabilir ve tasarruflu sistemlerin tasarlanabilmesini sağlamak için tüm bu sistemlerin izlenip raporlanabilmesi.
- Oteldeki çalışanların yönetilebilmesini sağlayabilecek yapıya göre sistem tasarımı. Daha sonra eklenebilir olmalı.

## Not
Bu başlık altında yapmış olduğum tasarımları, bakış açımı ve bir sistem tasarlanırken nelere dikkat ettiğimi göstereceğim. Yarıda kalan çalışmalar olması dolayısıyla bazı noktalarda eksiklikler olabilir.

### Başlıklar

1) Frontend - Nextjs
2) Backend DB - Restful API - Swagger - NestJS
3) Backend Logger - Java Apache Kafka
4) Backend STM32 Communication - Java
5) Elektronik STM32 - C

Sistemin frontend kısmındaki tasarımlarını burada yürüttüğüm mantık altında şekillendireceğiz.

### Başlıkların Detaylandırılıp İçlerinin Doldurulması

## Frontend
Sadece kurgu çalışması yapıldı. Kurgu ile ilgili detaylar, Frontend klasörü içerisinde bulunabilir. Bir tasarım çalışması yapılmadı.

## Backend NestJS
```
1. device/
2. device-config-all-stm-free-function/
3. device-config-all-stm-module-partition/
4. device-config-all-stm-module-partition-pair/
5. device-config-all-stm-module-partition-pair-condition/
6. device-config-all-stm-module-partition-pair-condition-function/
7. device-config-all-stm-module-partition-condition/
8. device-config-all-stm-module-partition-condition-virtual/
9. device-config-basic/
10. device-config-knx/
11. device-config-rs485/
12. device-config-schematic/
13. device-config-schematic-room/
14. device-room/
15. env/
16. java-communication/
17. otel-config/
18. otel-config-bacnet/
19. room/
20. room-config/
21. room-guest/
22. room-log/
23. room-log-device/
24. room-staff/
25. typeorm/
```

## Backend Java STM32 Communication
```
.
├── Certs
│   └── ...
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── bbsm
│   │               ├── BackTrigger
│   │               │   ├── RecvTrigger
│   │               │   └── SendTrigger
│   │               ├── DBConn
│   │               ├── Global
│   │               ├── RecvController
│   │               ├── Resources
│   │               ├── SendController
│   │               ├── Server
│   │               │   ├── FirstConnectRules
│   │               ├── Structs
│   │               │   ├── Device
│   │               └── TimeUpdate
│   └── test
....
```

En önemli kısımlarımız Java STM32 Communication ve Backend NestJS kısımlarımız. Bu iki kısım, tüm sistemin nasıl şekilleneceğini gösteriyor. Anlatımı kolaylaştırması açısından sadece klasörleri bıraktım.

## Backend Logger - Java Apache Kafka
Bu kısımın var olmasının sebebi, sistemin geliştirilebilirliğinin başarılı bir şekilde inşa edilebilmesidir. Var olan sistem loglarının tek bir elden yönetilebilmesini sağlayan yapısı, veri merkezleri farklı bile olsa bunları birleştirmek, işlemek ve dağıtmak için kolaylık sağlar. Web etkinliklerini takip etmek, sistem içerisinde verinin nasıl bir yolculuk yaptığını takip etmek, her bir anın ne kadar fazla yük oluşturursa oluştursun yönetilebilmesini sağlamak gibi özellikleri vardır. Ancak, bu özelliklerin her birini farklı teknolojilerle de yönetebilirdik. Buradaki asıl amaç, daha sonra ot

el sayıları çoğaldığında tüm verilerin ve logların uzak bir sunucuda tutulmasını istenirse, birden fazla otelin loglarının tek bir elden bir sunucuda işlenmesi için sunduğu kolaylıktır.

### Oluşturulacak Topicler
Bu kısım için henüz bir planlamam yok. Ancak, başlıkların neler olacağına ve nelere dikkat edilmesi gerektiğine dair bir planlama yapmış bulunmaktayım.

**Oluşturulacak topicler için başlıklar:**
- Web ve tablet arayüzlerinde yapılacak işlemlerin takibi.
- STM32 içerisindeki hareketlerin takibi.
- Sistem içerisinde hareket halinde olan mesajların takibi.
- Sistem içerisinde hareket halinde olan mesajların değişimlerinin takibi.
- Olası hataların takibi.

Loglama konusu çok ciddi bir konudur ve ne kadar ciddiye alındığına bağlı olarak bu proje bazında veya projenin tamamı kadar büyük olabilecek bir başlıktır. Bizim yapmayı planladığımız kısım, sadece ve sadece sistemin genel hata ayıklaması gibi çalışacak bir loglama. Veri nereden girildi, ne girildi, nereye gitti, bir hata çıktısı oluşturmuş mu, hangi kullanıcı hangi işlemi yaptı, STM32'miz buna nasıl bir karşılık verdi gibi bu işin küçük bir parçasını yapmak olacaktı.

Dediğim gibi, burada böyle bir teknolojinin kullanılmasındaki amaç, gelecekteki geliştirmeler için bir alan bırakmaktır.

Burada oluşacak topiclerin sayısı da bu nedenle oldukça az olmasını bekliyordum. Her bir alanımız için 3 ya da 4 topic maksimum. Yaklaşık 12 topic falan olacaktı.

Loglama ve dağıtık sistemleri konu alan birçok tez var. Beğendiğim bazı kaynakları buraya bırakacağım. Birçok farklı konuya değiniyorlar.
[Murak Koca'nın Doktora Tez Çalışması](https://tez.yok.gov.tr/UlusalTezMerkezi/TezGoster?key=RjZwH00oMG4iNa5Sgvlggz8LNOyM8hW0qnGPqs5nlNlSDJ9uEDbVwJwU2l8UYHpl)

## Klosör Amaçları Öncesi Config Mantığı 

Configlerimiz 3 ana aşamadan oluşacaktı:
1) STM32 ile doğrudan haberleşecek tüm aygıtların yapılarının tek tek listelenip bir kütüphane oluşturulması.
    - Tüm aygıtların kendi türlerine özgü olacak şekilde DP (data point) lerinin çıkarılması. Birden fazla fonksiyonu destekliyorsa, tek tek tüm fonksiyonları ve DP'lerini çıkarılması.
    - Örnek olarak: KNX uyumlu cihazlar için ETS yazılımı kullanarak aygıt verilerinin alınması. Kendi sistemimize uygun olacak şekilde veri yapılarımıza uygun hale getirilmesi.
2) Odalarda bulunan düzenlerin şematiklerinin ayrı ayrı çıkarılması
    - KNX uyumlu cihazlar için bir şematik oluşturma.
    - RS485 uyumlu cihazlar için bir şematik oluşturma.
    - Normal aygıtlar için bir şematik oluşturma.
    - Giriş (input) ve çıkış (output) cihazlarının eşleştirilmesi.
Burada bahsedilen şematiklerin amacı, var olan aygıt sıralamasını öğrenerek isimlendirmesini yapılabilmesi, bunu yaparak daha sonradan her odaya özgü tasarımlar yapabiliriz. Normal aygıtlar için hangi pine bağlanabileceklerini oteldeki kurulumu yapan kişiye bildirilmesi. KNX ve RS485 hatları için fiziksel adres gibi özelliklerin STM32 içerisinde doğru bir şekilde konfigüre edilebilmesini sağlanabilmesi. Web arayüzü üzerinden hiç otelde bulunmadan gerekli düzenlemelerin yapılabilmesi. İlk kurulum için işleri hızlandırma ve 900 odalı oteller gibi yerler için kullanılabilir bir sistem tasarlamayı mümkün hale getirmesi. İlk kurulumdan sonraki süreçte istenildiği anda ek cihaz eklenip cihazın devre dışı bırakılabilmesinin sağlanabilmesi.

3) Her odaya özgü istenilen yetkinliklerin kazandırılabilmesi amacıyla koşulların (conditions) ayarlanması.
   - Örnek olarak, odada bulunan ışıkların müşteri varken ve yokken gibi durumlar ile birlikte zaman ayarlamalarının yapılabilmesi. (Müşteri odadan çıktıktan 10 dakika sonra açık ışıkları kapatmak)
   - Klima, perde vb. tüm cihazlar için tek tek zaman ayarlamaları.
   - Her cihazın çıktısının ya da girişinin adlandırılarak işlenebilir hale getirilmesi.

Burada bahsedilmesi gereken bir başka strateji, STM32 içerisinde oluşturacağımız sensör yapısının burada bahsedilen config yapısına nasıl uyarlanacağıdır.

En basit şekilde anlatmak gerekirse, hem geliştirilebilirliği sağlamak hem de kolay bir şekilde yönetebilmek amacıyla STM32 içerisinde boşta duran fonksiyon yapıları oluşturulur. 
Mesela, bir odamızda bir ısı sensörümüz ve bir varlık sensörümüz var.

Sırasıyla oluşturulan configler ile şu işlemler yapılacak:

Isı sensörünün hangi tür olduğu ve hangi sıra ile bağlandığı bilgisi STM32'ye gider. STM32 buradan veri okumayı başarır. 
- Buradan elde edilen verinin bir string karşılığı olur. "SıcaklıkSıfır" ve bunun için bir koşul listesi belirlenebilir.
- Örnek koşullar:
    - Sıcaklık değeri 22'nin altında mı? Bu bilgi STM32'ye "SıcaklıkSıfır < 22 : conditionSıcaklık0" olarak gider.
    - Sıcaklık değeri 22 ile 24 arasında mı? Bu bilgi STM32'ye "SıcaklıkSıfır >= 22 && SıcaklıkSıfır <= 24 : conditionSıcaklık1" olarak gider.
Varlık sensörünün hangi tür olduğu ve hangi sıra ile bağlandığı bilgisi STM32'ye gider. STM32 buradan veri okumayı başarır.
- Buradan elde edilen verinin bir string karşılığı olur. "VarlıkSensörüSıfır" ve bunun için bir koşul listesi belirlenebilir.
    - Varlık Sensörü Durumları da isimlendirilir: "VarlıkSensörüPozitif", "VarlıkSensörüNegatif".

Şimdiye kadarki aşamalarda STM32'miz odalarda hangi sensörlerin olduğunu, isimlerini, konumlarını ve oluşturacakları durumların isimlendirilmesini uzaktan bir şekilde işlemiş olacak.

Sanal Sensörler:
Bu aşamaya kadar elimizde olan sensörlerin oluşturacağı durumları indeks değerleri olarak Map yapısına benzer şekilde alabiliriz.
Bu noktada başka bir ihtiyaç doğuyor. 
Sürekli bir şekilde almadığımız verilerin koşullarına ihtiyaç duyuyor oluşumuz.
Mesela, bir özel müşterinin ya da otelde çalışan elemanların bir işlemin koşullarımı etkilemesi gerekliliği. Örnek olarak, temizlik mesajı personele iletildi ama temizlik yapılmadı. Bu durum, benim sensörlere emir gönderirken dikkat etmem gereken bir özel durum oluşturabilir.

Buna da Sanal Sensör adını verdiğimiz yapılar sayesinde yapacağız.
İlk başta boşta duran fonksiyonlardan söz etmiştik. 
Burada back-end'den bilgi talep et gibi özel bir fonksiyon olabilir. 
Belirlenmiş string karşılıkları ile her özel duruma karşı bir indeks değerinin 
STM32 içerisindeki kodu değiştirmeden alınıp doğru bir şekilde işlenebilmesi.

Örnek:
"index:TemizlikPozitif,TemizlikNegatif:Temizlik_durum" olarak STM32'ye iletildiğinde STM32'nin burada olan bilgileri DP'sine göre Temizlik_durum ile eşleştirmesi.
Bunu bir sensör gibi kendi içinde kaydetmesi. Daha sonra aynı başlıktan bir bilgi talep edebilir ve bir bilgi gönderebilir konumda olmuş olacak.

Şu ana kadarki aşamalar ile yapabildiklerimiz:
- Herhangi bir sensör veya aygıta istediğimiz bir şeyi yaptırabiliyoruz. Aldığımız verileri indeks değerleri ya da istediğimiz ifadelere göre durumlarını oluşturabiliyoruz.

Bu aşamalar başarılı şekilde yapıldıktan sonra, oluşturduğumuz koşulların kendileri de dahil olmak üzere diğer sensörleri ve aygıtları etkileyebilmesini sağlamak.

Bu aşama için yapılması gerekenler:
Şu anda bir KNX uyumlu klimayı göz önüne alalım, içerisinde birden fazla fonksiyonu destekleyebilen bir yapı var. STM32 içerisinden bu aygıta bir veri göndereceğimiz zaman, bize sağladığı özellikleri kullanırız.
Burada hangi fonksiyonu hangi DP ile kullanmamız gerektiği bellidir ya da diğer aygıtlar içinde aynısı düşünülebilir. Nasıl bir aygıt olursa olsun, hangi mesajı/veriyi gönderdiğinizde ne olması gerektiğini bilirsiniz.
Eğer bunu yapabiliyorsanız, bunu isimlendirebilirsiniz demektir.
Zaten bu verileri config'in içerisine gömmüştüm. STM32 içerisinde de aldığım config verilerine göre bu aygıta istediğimi yaptırabilecek yetkinliğe sahip kodlarım var. Varsayım tabii ki :)

Tek yapmam gereken, hangi durumda hangi işlemi yapması gerektiğini söylemek olacak.

```
"KNX-KLİMA"        - "Klima Aç, Klima Kapat"               - {"SıcaklıkSıfır:conditionSıcaklık0 ve VarlıkSensörüSıfır:VarlıkSensörüPozitif", "SıcaklıkSıfır:conditionSıcaklık0 ve VarlıkSensörüSıfır:VarlıkSensörüPozitif"}
sensör/aygıt ismi  - Backend'de tanımlanmış davranış. Burada bir seçim yapabileceğiniz bir panel hayal edin front-end'de    - koşullar
                     yapılan seçime göre arka planda veritabanından gerekli bilgileri çekecek.
```
Aynı

 şekilde sanal sensörlere bağlı sanal koşullar da eklenebilir.

---

Tüm bu config aşamaları adlandırılıp kaydedilebecek şekilde tasarlanacak. Bir odada beğendiğiniz bir configi istediğiniz odalara atayabilme.

## Dökümantasyon
- Nestjs için swagger
- javalar için Javadoc
- c kodları için Doxygen (çoğunlukla boş fonksiyonlar ve structların yapıları için bilgi verecek)

## Haberleşme yapısı.
- Next.js               - NestJS                               Ssl Http - Socket
- Next.js               - JavaLoger                            Socket
- Nestjs                - JavaLoger                            Topic Http
- Nestjs                - JavaStm32Communaction                Socket
- JavaStm32Communaction - JavaLoger                            Topic Http
- JavaStm32Communaction - Stm32                                Ssl Socket

## Database yapısı
Database için PostgreSQL kullanılacak.
- Database yapılarını içeren fotoğraflar yüklenecek. Düzenlemelerini yaptıktan sonra.
- Tamamı olmasada küçük bir kısmı inşa edildi.

## Sistem Entegrasyon
Planlanan yapı her başlık bir docker olarak kaldırılacak. Diğerler ile bağlantılar env dosyaları ile yönetilecek. Bir VMDK dosyası halinde image olarak taşıması yapılacak.
Olası çökme durumlarda müdhale edecek yapıları docker araçlarını kullanarak yapma. Veri yedekleme konuları için bir VMDK daha kaldırılıp ekstra önlem alınabilir. Belirli bir saat aralığında Database in yedeklenmesi.

## Network
Çok önemli bir başlık olmasına rağmen detaylı bir fikir yürüttemediğim bi konu. Kullancağım ağ sadece benim cihazlarımın haberleşmesi için olan bir ağ olduğundan, cihazlarımın kendi aralarında haberleşme gereksinimi duymamasından.
Backend ile var olan yükün çoğu ilk bağlantı aşamsında yaşanacak ve daha sonrasındada verinin backende ulaşmasında bir aciliyet olmaması süreci yönetmeyi kolaylaştıracaktır. En kötünün kötü durumunda bile çok basit yöntemlerle sürecin olumsuz etkilenmemesi sağlanabilir. Örnek olarak cihazların backende bilgi göndermesi sıra ile gerçekleştirilebilir. ilk başta bir istek atarlar istekler sıraya koyulur. O sıraya göre veri gönder emri verilir.
Bu şekilde Backenden gelecek olan bir veriyi de hızlı bir şekilde transfer edebilirim.

## Güvenlik
Java Stn32 arasında olan bağlantı SSL ile sağlanacak. Açık Anahtarlı Şifreleme yöntemide kullanılarak veri iletimi yapılacak.
Web için standart olan tüm güvenlik önlemleri alınacak. JWT vs 
Firewall Kullanımı gibi basit önlemlerde alınacak. Güvenli ağ bağlantıları ile sadece izin verilen ağ ların ulaşabilmesi sağlanacak.

## Sistem inşa süreç önizleme

## Klosör yapıların var oluş amaçları.

## Sistem tasarımnın eksiklikleri
## Hiç bahsedilmemiş düşünülmemiş kısımlar.

Vakit buldukça ekleme yapmaya devam edeceğim.
