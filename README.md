# OtelOtamasyonTaslak
Bir otel otamasyon sistemi tasarımı. Daha önce fiyatını verdiğimiz fakat alamadığımız bir iş için başlangıç çalışmaları. Yarıda kesilmek zorunda kalan bir çalışmadır. 
Yinede yaptığım çalışmaları paylaşacağım. Projede beraber ilerlemek isteyen elektronik bilen, web bilen ,stm32, mobil kodlayabilecek arkdaşlar ulaşırlar ise beraber ilerleriz.

## Genel Amaç ve Yapılacaklar
- Bir otelde bulunan tüm odaların akıllı hale getirilerek sistemlerin otonom beceri kazanmalarını sağlamak.
- Otelde bulunan çalışanların bu sisteme entegre bir biçimde çalışmalarını sağlayabilecek sistemlerin tasarlanması.
- Daha öncede otelde bulunan sistemlere entegre bir biçimde çalışabilmesi.
- Odalarda bulunan lamba, klima, priz, perde gibi yapıların sisteme uygun hale getirilmesi.
- Otel içinde bulunan klimaların yada benzeri sistemlerin sisteme entegre şekilde otonom hale getirilmesi.
- Knx rs485 bacnet başta olmak üzere gibi uyumlu cihazların sisteme entegre şekilde çalışmalarının sağlanması.
- Otel içinde bulunan tevizyon, çalışan tabletleri gibi farklı cihazların sisteme entegre şekilde çalışabilmeleri.
- Tüm bu sistemlerin izlenebilmesinin sağlanabilmesi için web arayüzü üzerinden izleme sistemlerini tasarlanması.
- Otel odalarında bulunan farklı senaryolara uygun halde çalışabilmesi için config sistemi tasarlanması. Knx uyumlu cihazlar gibi sistemlere uygun halde çalışmalarının sağlanması.
- Otel ağ yapılandırmalarının yapılması.
- Tek bir sistem üzerinden hem çalışanların yönetilebilmesi. Hemde üretilen verinin kontrolü.
- Sistemin geliştirilebilir bir yapı üzerine oturtulması ve üretilen her kodun dökümantasyonunun yapılması.
- Config yapısının çok modüler bir şekilde inşa edilmesi.
- Knx gibi cihazlar için Ets yazılımının ürettiği database kullanılarak. Ets yazılımını direk kulllanmadan çalışabilecek sistemin tasarlanması.
- Config tassarımın detaylı ve kolay bi şekilde yapılandırabilmesini sağlayarak. Üretilen configlerin kolay bir şekilde STM32 içinde çalışabilmesini sağlamak. Web arayüzünden Config tasarımı yapılacak ve bu stm32 içinde direk çalışabilecek.

## Sisteme genel bir bakış:
Otelimizin her odasısnın yapısının farklı olduğunu düşünelim. Her odada KNX uyumlu, RS485 uyumlu cihazlarımız var. Varlık sensörleri, lamba ,klima gibi farklı yapılarımız mevcut. 
Böyle bir otelde her odaya uyumlu halde çalışabilecek. Odaların kontrollerini sağlayabilmek. En genel amacımız. Bir örnek vermek gerekirse. 
- Bir müşteri odadan çıktıktan sonra lambaları otamatik kapatacak. Klimayı otamatik kapatacak bir sistem istiyorsunuz
. Müşteri odadan çıkmadan önce elindeki telefonunda odamın temizlenmesini istiyorum diyebilmeli ve müşteri odadan çıktıktan sonra o işle ilgilenen personele otamatik bir bildirim  gitmeli.
- Müşteri elindeki telefonunda odadaki herhangi bir lambayı yada klimanın ayarını değiştirebilmeli .Tüm bunları ve daha fazlasını yapabilecek bir sistem.
- Otelin içerisindeki enerji verimliliğini takip ederek gelecekte daha yaşanabilir daha tasaruflu sistemlerin tasarlanabilmesini sağlamak için tüm bu sistemlerin izlenip raporlanmasını görebilmek.
- Oteldeki çalışanların yönetilebilmesini sağlayabilmek için sağlayabilecek yapıya göre sistem tasarımı. Daha sonra eklenebilir olmalı.

## Not
Bu başlık altında yapmış olduğum tasarımları. Bakış açımı. Bir sistem tasarlanırken nelere dikkat ettiğimi göstereceğim. Yarıda kalan çalışmalar olması dolayısı ile bazı noktalarda eksiklikler olabilir.

### BAŞLIKLAR

1) Frontend                                                     Nextjs
2) Backend     DB - Restful Api - Swagger                       NestJS
3) Backend     Loger                                            Java Apache Kafka
4) Backend     STM32 Communaction                               Java 
5) Elektronik  Stm32                                            c

Sistemin frontend kısmındaki tasarımlarını burada yürüttüğüm mantık altında şekkillendiriyor olacağız.

### Başlıkların detaylandırılıp içlerinin doldurulması

## Frontend
Sadece kurgu çalışması yapıldı
Kurgu ile ilgili detaylar. Frontend klosörü içerisinde bulabilirsiniz.
Bir tasarım çalışması yapılmadı. 

## Bacnkend NestJS
```
1. device/
2. device-config-all-stm-free-function/
3. device-config-all-stm-modüle-partition/
4. device-config-all-stm-modüle-partition-pair/
5. device-config-all-stm-modüle-partition-pair-condition/
6. device-config-all-stm-modüle-partition-pair-condition-function/
7. device-config-all-stm-modüle-partition-condititon/
8. device-config-all-stm-modüle-partition-condititon-virtual/
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

## Backend JavaStm32Communaction
```
.
├── Certs
│   └── ...
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── bbsm
│   │               ├── BackTrigger
│   │               │   ├── RecvTrigger
│   │               │   └── SendTrigger
│   │               ├── DBConn
│   │               ├── Global
│   │               ├── RecvController
│   │               ├── Resources
│   │               ├── SendController
│   │               ├── Server
│   │               │   ├── FirstConnectRules
│   │               ├── Structs
│   │               │   ├── Device
│   │               └── TimeUpdate
│   └── test
....
```

En önemli kısımlarımız javaStm32Communaction ve Backend NestJS ksıımlarımız. Bu iki kısımdaki yapılar tüm sistemin nasıl şekilleneceğini gösteriyor.
Anlatımı kolaylaştırması açısından bir tek klosörleri bıraktım.

## Backend     Loger                                            Java Apache Kafka
 Bu kısmın var olmasısın sebebi. Sistemin geliştirilebilirliliğinin başarılı bir şekilde inşa edilebilmesi. Aslında var olan tüm güzelliklerini kullanmayacağız.
- Var olan sistemin loglarının tek bir elden yönetilebilmesini sağlayan çok güzel bir yapısı var. 
- Veri merkezleri farklı bile olsa bunları birleştirmek işlemek ve dağıtmak bu yapıyla fazlasıyla kolaylaşıyor.
- Web aktivetelerini takip edebilmek.
- Sistem içerisinde verinin nasıl bir yolculuk yaptığını takib edebilmek.
- Her bir anın ne kadar fazla yük oluşturursa oluştursun yönetilebilmesini sağlamak.
- Fakat bu sebeblerin her birini farklı teknolojilerlede yönetebilirdik.
- Burada asıl amaç daha sonra otel sayıları çoğaldığında tüm verilerin logların uzak bir sunucuda tutulması istenirse. 
- Birden fazla otelin logları tek bir elden bir sunucuda işlenmek istenirse sunduğu kolaylık.

### Oluşturulacak Topicler
Bu kısım için henüz bir planlamam yok. Fakat başlıkların neler olacağı nelere dikkat edilmesi gerekildiğinin planlamsını yapmış bulunmaktayım.

**Oluşturulacak topicler için başlıklar.**
Web ve tablet arayüzlerinde yapılacak işlemlerin takibi.
Stm32 içerisinde hareketlerin takibi.
Sistem içerisinde hareket halinde olan mesajların takibi.
Sistem içerisinde hareket halinde olan mesajların değişimlerinin takibi.
Olası errorler in takibi.

Loglama konusu çok ciddili bir  konudur ve ne kadar ciddiye alındığına bağlı olarak bu proje bazlı bu projenin tamamı kadarda büyük olabilecek bir başlıktır.
Bizim yapmayı plandığımız kısım sadece ve sadece sistemin genel debugu gibi çalışacak bir loglama. Veri nereden girildi ne girildi nereye gitti bir hata çıktısi oluştumu. Hangi kullanıcı hangi işlemi yaptı stm32 miz buna nasıl bir karşılık verdi gibi bu işin küçük bir parçasını yapmak olacaktı.

Dediğim gibi burada böyle bir teknolojinin kullanılmasındaki amaç gelecekteki geliştirmeler için bir alan bırakmak.

Burada oluşacak topiclerin sayısıda bu nedenle epey bir az olmasını bekliyordum. 
Her bir alanımız için 3 yada 4 topic maksimum.
Yaklaşık 12 topic falan olacaktı.

Loglama ve dağıtık sistemleri kaleme alan bir çok tez var. Beğendiğim bazı kaynakları buraya bırakacağım. Bir çok farklı konuya değiniyor.
[Murak Koca'nın Doktara tez çalışması](https://tez.yok.gov.tr/UlusalTezMerkezi/TezGoster?key=RjZwH00oMG4iNa5Sgvlggz8LNOyM8hW0qnGPqs5nlNlSDJ9uEDbVwJwU2l8UYHpl)

## Klosör amaçları öncesi config mantığı 

Configlerimiz 3 ana aşamadan oluşacaktı.
1) Stm32 ile direk haberleşecek tüm aygıtların yapıların tek tek listelerinin çıkarılıp bir kütüphane oluşturulması.
    - Tüm aygıtların kendi türlerine özgü olacak şekilde DP(data point) lerinin çıkarılması. Birden fazla fonksiyonu destekliyorsa tek tek tüm fonksiyonları ve DP lerini çıkarılması.
    - Örnek olarak: KNX uyumlu cihazlar için ETS yazılımı kullanarak aygıt verilerinin alınması. Kendi sistemimizie uygun olacak şekilde veri yapılarımıza uygun hale getirilmesi.
3) Odalarda bulunan düzenlerin şematikelrinin ayrı ayrı çıkarılması
    - Knx uyumlu cihazlar için bir schmeatik oluşturma.
    - Rs485 uyumlu cihazlar için bir şematik oluşturma.
    - Normal aygıtlar için bir şematik oluşturma.
    - İnput ve Output cihazlarının eşleştirilmesi.
Burada bahsedilen şematikerin amacı var olan aygıt sıralamasını öğrenerek isimlendirmesini yapılabilmesi bunu yaparak daha sonradan her odaya özgü tasarımlar yapabilir. Normal aygıtlar için hangi pine bağlanabileceklerini oteldeki kurulumu yapan kişiye bildirilmesi. KNX ve RS485 hatları için fiziksel adres gibi özelliklerin stm32 içerisinde doğru bir şekilde configüre edilebilmesini sağlanabilmesi. Web arayüzü üzerinden hiç otelde bulunmadan. Gerekli düzenlemelerin yapılabilmesinin sağlanabilmesii. İlk kurulum için işleri hızlandırma ve 900 odalı oteller gibi yerler için kullanılabilir bir sistem tasarlamayı mümkün hale getirmesi. İlk kurulumdan sonraki süreçte istenildiği anda ek cihaz eklenip cihaz devre dışı bırakılabilmesinin sağlanabilmesi.
4) Her odaya özgü istenilen yetkinliklerin kazandıralabilmesi amaçlı condititonların ayarlanması.
   - Örnek olarak odada bulunan ışıkların müşteri varken ve yokken gibi durumlar ile birlikte zaman ayarlamarının yapılabilmesi. (müşteri odadan çıktıktan 10 dakika sonra açık ışıkları kapatmak)
   - Klima, perde vs tüm cihazlar için tek tek zaman ayarlamaları.
   - Her cihazın çıktısının yada inputunun adlandırılarak işlenebilir hale getirilmesi.

Burada bahsedilmesi gerekilen bir başka stratereji.
STM32 içiresinde oluşturacağımız. Sensör yapısnın burada bahsedilen config yapsınıa nasıl uyarlanacağı.

En basit şekilde anlatmak istenilirse. Hem geliştirilebilirliği sağlamak ve kolay bir şekilde yönetebilmek amaçlı.
Stm32 içerisinde boşta duran fonksiyon yapıları oluşturmak. 
Mesala bir odamızda bir ısı sensörümüz ve bir varlık sensörümüz var.

Sırasıyla oluşturulan configler ile şu işlemler yapılacak.

Isı sensörünün hangi tür olduğu ve hangi sıra ile bağlandığı bilgisi stm32 ye gider. Stm32 buradan veri okumayı başarır. 
- Buradan elde edilen verinin bir string karşılığı olur. "SıcaklıkSıfır" ve bunun için bir condititon listesi belirlenebilir.
- Örnek condititonlar
    - Sıcaklık değeri 22 nin altındamı. Bu bilgi stm32 ye "SıcaklıkSıfır < 22 : condititonScıaklık0 "olarak gider. 
    - Sıcaklık değeri 22 ile 24 içerisindemi. Bu bilgi stm32 ye "SıcaklıkSıfır >= 22 && SıcaklıkSıfır <= 24 : condititonScıaklık1"  olarak gider.
Varlık sensörünün hangi tür olduğu ve hangi sıra ile bağlandığı bilgisi stm32 ye gider. Stm32 buradan veri okumayı başarır. 
- Buradan elde edilen verinin bir string karşılığı olur. "VarlıkSensörüSıfır" ve bunun için bir condititon listesi belirlenebilir.
    - Varlık Sensörü Durumları da isimlendirilir "VarlıkSensörüPozitif" , "VarlıkSensörüNegatif" 

Şimdiye kadarki aşamlarda stm32 miz Odalarda hangi sensörlerin olduğunu. İsimlerini konumlarını oluşturacakları durumların isimlendirlmesini uzaktan bir şekilde işlemiş olacağız.

Sanal Sensörler.
Bu aşamaya kadar elimizde olan sensörlerin oluşturacağı durumları index değerler olarak Map yapısına benzer şekilde alabiliyoruz.
Bu noktada başka bir ihtiyaç doğuyor. Sürekli bir şekilde almadığım verilerin condititonlarına ihtiyaç duyuyor oluşum.
Mesala bir özel müşterinin yada otelde çalışan elemanların bir işlemin condititonlarımı etkilemesi gerekliliği. Örnek temizlik mesajı personele iletildi ama temizlik yapılmadı. Bu durum benim sensörlere emir gönderirken dikkat etmem gereken bir özel durum oluşturabilir.

Bunada Sanal Sensör adını verdiğim yapılar sayesinde yapacağız.
İlk başta boşta duran fonksiyonlardan söz etmiştik. 
Burada backenden bilgi talep et gibi özel bir fonksiyon olabilir. 
Belirlenmiş string karşılıkları ile her özel duruma karşı bir index değerin 
Stm32 içerisindeki kodu değiştirmeden alınıp doğru bir şekilde işlenebilmesi.

Örnek:
"index:TemizlikPozitif,TemizlikNegatif:Temizlik_durum", olarak stm32 ye iletildiğnide stm32 nin burada olan bilgileri Dp sine göre Temizlik_durum ile eşleştirmesi.
Bunu bir sensör gibi kendi içinde kaydetmesi. Daha sonra aynı başlıktan bir bilgi talep edebilir ve bir bilgi gönderebilir konumda olmuş olacak.

Şu ana kadarki aşamalar ile yapabildikerimiz 
- Herhangi bir sensör, aygıt'a istediğimiz bir şeyi yaptırabiliyor. Aldığımız verileri index değerler yada istediğimiz ifadelere göre durumlarını oluşturabiliyoruz.

Bu aşamalar başarılı şekilde yapıldıktan sonra oluşturduğumuz condititionların kendileride dahil olmak üzere diğer sensörleri aygıtları etkileyebilmesini sağlamak.

Bu aşama için yapılması için gerekilenler.
Şuan bir knx uyumlu bir klimayı göz önüne alalım içerisinde bir den fazka fonksiyonu destekleyebilen bir yapı var. Stm32 içerisinden bu aygıta bir veri göndereceğimiz zaman bize sağladığı özellikleri kullanırız.
Burada hangi fonksiyonu hangi DP ile kullanmamız gerektiği bellidir yada diğer aygıtlar içinde aynısı düşünülebilir nasıl bir aygıt olursa olsun hangi mesajı/veriyi gönderdiğinizde ne olması gerektiğni bilirsiniz.
Eğer bunu yapabiliyorsanız. Bunu isimlendirebilirsinizde demek oluyor.
Zaten bu verileri configin içerisine gömmüştüm. STM32 içerisindede aldığım config verilerine göre bu aygıta istediğimi yaptırabilecek yetkinliğe sahip kodlarım var. Varsayım tabiki :)

Tek yapmam gereken hangi durumda hangi işlemi yapması gerektiğini söylemek olacak.

```
"KNX-KLİMA"        - "Klima Aç, Klima kapat"               - {" SıcaklıkSıfır:condititonScıaklık0 ve  VarlıkSensörüSıfır:VarlıkSensörüPozitif " ," SıcaklıkSıfır:condititonScıaklık0 ve  VarlıkSensörüSıfır:VarlıkSensörüPozitif "}
sensör/aygıt ismi  - Backendde  tanımlanmış davranış. burada bir seçim yapabileceğiniz bir panel hayal edin frontendde    - condititonlar
                     yapılan seçime göre arka planda databaseden gerekli bilgileri çekecek.
```
Aynı şekilde sanal sensörlere bağlı sanal condititonlarda eklenebilir.

### **Burada bahsedilen Config STM32 straterejisi nin çalışabilrliği test edilmiş ve çalışan bir algoritma ortaya konulmuştur. Ekonmoik kaygılardan dolayı paylaşılmayacaktır. C kodu olarak test edilmiş. STM32 ye geçirlilmemiştir. STM32 ye uyarlanabilecek şekilde düşünülerek kod'lar yazılmıştır**
### **Yapıldı diye bahsedilen kısım. Uzun uzun anlattığım condititonlara bağlı olan yapıdır. Uzaktan bir şekilde sanki stm32 den veri çekiliyor txt den zamana bağlı veriler çekilmiş. javadada nestjs den geliyormuş gibi el ile veriler Postmanden gönderdiğim bilgiler şeklinde stm32 ye iletilmiş c kodunda oluşturulmuş boş fonksiyonlar ile belirli durumlar gerçekleştiğinde çalışacak olan yapılar yapılmıştır. Oluşturulacak sensörlerin/aygıtların belirli bir knx dökümanı baz alınarak. el ile basit bir knx hattı oluşturulmuş. Basit sensörler/aygıtlar oluşturulmuş isimlendirmeler yapılmış. Algoritmanın doğru bir şekilde nasıl çalışacağı eksiklikleri ve database girilmesi gerekilen bilgiler netleştirilmiştir.**

Tüm bu config aşamaları adlandırılıp kaydedilebecek şekilde tasarlanacak. Bir odada beğendiğiniz bir configi istediğiniz odalara atayabilme.

## Dökümantasyon
- Nestjs için swagger
- javalar için Javadoc
- c kodları için Doxygen (çoğunlukla boş fonksiyonlar ve structların yapıları için bilgi verecek)

## Haberkeşme yapısı.
Next.js               - NestJS                               Ssl Http - Socket
Next.js               - JavaLoger                            Socket
Nestjs                - JavaLoger                            Topic Http
Nestjs                - JavaStm32Communaction                Socket
JavaStm32Communaction - JavaLoger                            Topic Http
JavaStm32Communaction - Stm32                                Ssl Socket

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

