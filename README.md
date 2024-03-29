İş başvuruları yapmam sebebi ile repo public durumda fakat içerikler daha düzenlenmiş bir şekilde değil.

Almaya çalıştığımız fakat bazı sebeblerden ötürü yaptığım çalışmaları gösteremediğim çalışmalarım. İmage klosöründeki "genel yapi.jpeg" adlı fotoğraf dışında firmanın başka bir yönlendirmesi yada yardımı olmamıştır. Aşağıda gösterdiğim çalışmalarımda . Yapı çok genel bir yapı olduğu için koymakta bir sakınca görmedim.

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
- KNX gibi cihazlar için ETS 5 yazılımının ürettiği veritabanı kullanılarak, ETS 5 yazılımını doğrudan kullanmadan çalışabilecek bir sistemin tasarlanması.
- Config tasarımının detaylı ve kolay bir şekilde yapılandırılması, üretilen configlerin kolay bir şekilde her oda içinde kullanılacak STM32 içinde çalışabilmesi sağlanacak. Web arayüzünden config tasarımı yapılacak ve bu STM32 içinde doğrudan çalışabilecek.

## Sisteme Genel Bakış
Otelimizin her odasının yapısının farklı olduğunu düşünelim. Her odada KNX ,RS485 vb uyumlu cihazlarımız var. Varlık sensörleri, lamba, klima gibi farklı yapılarımız mevcut. Böyle bir otelde her odaya uygun şekilde çalışabilecek odaların kontrollerini sağlamak en genel amacımızdır. Odaların statülerine göre özelleştirilmiş durumlar(vip,standart,ekonomik) Bir örnek vermek gerekirse:
- Bir müşteri odadan çıktıktan sonra lambaları otomatik kapatacak. Klimayı otomatik kapatacak bir sistem istiyorsunuz. Müşteri odadan çıkmadan önce telefonunda odanın temizlenmesini isteyebilmeli ve müşteri odadan çıktıktan sonra bu işle ilgilenen personele otomatik bir bildirim gitmeli.
- Müşteri telefonunda odadaki herhangi bir lambayı veya klimanın ayarını değiştirebilmeli. Tüm bunları ve daha fazlasını yapabilecek bir sistem.
- Otelin içerisindeki enerji verimliliğini takip ederek gelecekte daha yaşanabilir ve tasarruflu sistemlerin tasarlanabilmesini sağlamak için tüm bu sistemlerin izlenip raporlanabilmesi.
- Oteldeki çalışanların yönetilebilmesini sağlayabilecek yapıya göre sistem tasarımı. 

![](https://github.com/sametyldrmm/OtelOtamasyonSistemDizayn/blob/main/images/genel%20yapi.jpeg)
![](https://github.com/sametyldrmm/OtelOtamasyonSistemDizayn/blob/main/images/haberlesme.jpeg)
## Not
Bu başlık altında yapmış olduğum tasarımları, bakış açımı ve bir sistem tasarlanırken nelere dikkat ettiğimi göstereceğim. Yarıda kalan çalışmalar olması dolayısıyla bazı noktalarda eksiklikler olabilir.

### Başlıklar
1) Frontend - Nextjs
2) Backend DB - Restful API - Swagger - NestJS
3) Backend Logger -                  Java Apache Kafka
4) Backend STM32 Communication -     Java
5) Elektronik Yazılımı STM32 - C
6) Elektronik PCB Tasarımı Eagle

Sistemin frontend kısmındaki tasarımlarını burada yürüttüğüm mantık altında şekillendireceğiz.

### Başlıkların Detaylandırılıp İçlerinin Doldurulması

## Frontend
Az sayıda sayfanın tasarımları figma üzerinden yapıldı. Ana tasarımın ortaya çıkması için. Figma tasarımlarımı eklenecektir.
Sadece kurgu çalışması yapıldı. Kurgu ile ilgili detaylar, Frontend klasörü içerisinde bulunabilir.

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

C kodları içinde bu şekilde dosya yapıları verilecek .h dosyaları ve .c dosya isimleri klosör yapıları. Daha sonra.

En önemli kısımlarımız Java STM32 Communication ve Backend NestJS kısımlarımız. Bu iki kısım, tüm sistemin nasıl şekilleneceğini gösteriyor. Anlatımı kolaylaştırması açısından sadece klasörleri bıraktım.

## Backend Logger - Java Apache Kafka
Bu kısımın var olmasının sebebi, sistemin geliştirilebilirliğinin başarılı bir şekilde inşa edilebilmesidir. Var olan sistem loglarının tek bir elden yönetilebilmesini sağlayan yapısı, veri merkezleri farklı bile olsa bunları birleştirmek, işlemek ve dağıtmak için kolaylık sağlar. Web etkinliklerini takip etmek, sistem içerisinde verinin nasıl bir yolculuk yaptığını takip etmek, her bir anın ne kadar fazla yük oluşturursa oluştursun yönetilebilmesini sağlamak gibi özellikleri vardır. Ancak, bu özelliklerin her birini farklı teknolojilerle de yönetebilirdik. Buradaki asıl amaç, daha sonra otel sayıları çoğaldığında tüm verilerin ve logların uzak bir sunucuda tutulmasını istenirse, birden fazla otelin loglarının tek bir elden bir sunucuda işlenmesi için sunduğu kolaylıktır.

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
Aynı şekilde sanal sensörlere bağlı sanal koşullar da eklenebilir.

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
- Nestjs                - JavaStm32Communication                Socket
- JavaStm32Communication - JavaLoger                            Topic Http
- JavaStm32Communication - Stm32                                Ssl Socket

## Database yapısı
Database için PostgreSQL kullanılacak.
- Javanın ve Nestjs in db leri farklı db ler olacak. Javanın db sinde stm32 ve oda ile alakalı bilgiler duracak. Nestjs nin databasinde kullanıcılar ile ilgili bilgiler duracak. Web içerisinde olacak olan işlemler için gerekli bilgiler.
- Nestjs hem Javanın db sine bağlanacak hem kendi db sine. Yerine göre ikisinide kullanacak.
- Otele ait bilgiler Otelin apileri aracaılığı ile alınacak. NestJs içerisinde yapılacak.

- Database yapılarını içeren fotoğraflar yüklenecek. Düzenlemelerini yaptıktan sonra.
- Tamamı olmasada küçük bir kısmı inşa edildi.
![](https://github.com/sametyldrmm/OtelOtamasyonSistemDizayn/blob/main/images/database.jpeg)
## Sistem Entegrasyon
Planlanan yapı her başlık bir docker olarak kaldırılacak. Diğerler ile bağlantılar env dosyaları ile yönetilecek. Bir VMDK dosyası halinde image olarak taşıması yapılacak.
Olası çökme durumlarda müdhale edecek yapıları docker araçlarını kullanarak yapma. Veri yedekleme konuları için bir VMDK daha kaldırılıp ekstra önlem alınabilir. Belirli bir saat aralığında Database in yedeklenmesi.

## Network
Çok önemli bir başlık olmasına rağmen detaylı bir fikir yürüttemediğim bi konu. Kullancağım ağ sadece benim cihazlarımın haberleşmesi için olan bir ağ olduğundan, cihazlarımın kendi aralarında haberleşme gereksinimi duymamasından.
Backend ile var olan yükün çoğu ilk bağlantı aşamsında yaşanacak ve daha sonrasındada verinin backende ulaşmasında bir aciliyet olmaması süreci yönetmeyi kolaylaştıracaktır. En kötünün kötü durumunda bile çok basit yöntemlerle sürecin olumsuz etkilenmemesi sağlanabilir. Örnek olarak cihazların backende bilgi göndermesi sıra ile gerçekleştirilebilir. ilk başta bir istek atarlar istekler sıraya koyulur. O sıraya göre veri gönder emri verilir.
Bu şekilde Backenden gelecek olan bir veriyi de hızlı bir şekilde transfer edebilirim.

## Güvenlik
Java Stm32 arasında olan bağlantı SSL ile sağlanacak. Açık Anahtarlı Şifreleme yöntemide kullanılarak veri iletimi yapılacak.
Web için standart olan tüm güvenlik önlemleri alınacak. JWT vs 
Firewall Kullanımı gibi basit önlemlerde alınacak. Güvenli ağ bağlantıları ile sadece izin verilen ağ ların ulaşabilmesi sağlanacak.

## Sistem İnşa Süreç Önizleme1
Şimdiye kadar yaptığım planlamalar ve kendi başıma yürüttüğüm süreç içerisinde. Kol adını verdiğim, bir verinin fronttendden stm32 ye kadar ki sürecinin NestJS, JavaStm32Communication, C test kodlarını yazmaktan ibaret.
Genel olarak sıralama ilk test aşamalarında.


Postman -> Nestjs -> JavaStm32Communication -> C test kodu şeklinde olacak.
           Nestjs -> JavaLogger
                    JavaStm32Communication -> JavaLogger

Ve bu sıralamanın ters bağlantıları.
- İlk olarak yapılması gereken şey genel yapının neye benzeyeceğinin iyice oturtulması.
- Daha sonrasıda birbirinden bağımsız parçaların ikili haberleşmelerini yapmak.
- Daha sonra birbirleri üzerinden haberleşmelerin yapılması ve Logger üzerinden takip edilmesi.

** Bu kısımda herşeyi bir bütün gibi ele alarak parçalamak gerekir.**

### Genel Yapının Anlaşılması
Bu aşamada kastettiğim şey yazı ile anlatılması çok zor bir şey. Şematikler ile çalışıyorum kendim. İlk başta şematiklerini çizip üzerlerinden gerekli class yapılarını ve dosya yapılarını belirliyorum. 
Tüm şematiklerimi ekleyeceğim. Şuan için düzenlenmeleri gerektiği için buraya atamıyorum.

İlk olarak anlaşılması gereken şey JavaStm32Communaction'a neden ihtiyaç duyuldğudur. 
NestJS üzerindenden yapamaz mıydık ? Aslında süreci uzatan bir başlık.

Kendimce sebeblerim :
- Java yapısının C ile haberleşmeye daha uygun olduğunu düşünmem.
- İşi planlama aşamsında iyi bir şekilde parçalayabilmek.
- Mikro servis mantığına uygun bir yapı hazırlayabilmek için Nestjs de ki yükü hafifletiyor. İnşa sürecinde var olan yapılacakları. Parça parça inşa edebilmek ve kontrolü kaybetmemek.
- İnşa sürecinde ekibimde olacak kişilerin javaya daha çabuk adapte olabileceklerini düşünmem.
- Hataları minimalize etmek istiyor oluşum. Olası bir Stm32 ile bağlantı kesilmesi. Çökme gibi durumların yaşanabilecek oluşu. Stm32 lerde sistemden kopma gibi durumlar ele daha çok alnacağı için. Testlerimizi parça parça hızlı bir şekilde gerçekleştiriyor olabileceğiz.

### Öncelik verilmesi gereken durumlar
- Java içerisinde ve stm32 içerisinde kullanabileceğimiz. Muhtemel veri yapılarının elimden geldiğince planlama aşamasında belirleyebilmek istemem.
- Sistemin ana odağı Stm32 lere göndermeyi planladığımız. Config mantığı olacağı için. Verilerin içine alınabileceği yapılar içleri boş dahi olsa belirlenebilmesi.
- Config mantığının algoritmasını belirleyebilmek. Düşüncelerimizin çalışacağından mümkün olduğunca emin olmaya çalışmak. Bunun için belli bir kısmınının c kodlarını yazıyor  ve testlerini yapıyorum. Burada yukarıda ve aşşağıda(c test kodu) bahsettiğim config mantığını test ettim.
- Birbirleri ile haberleşecek yapıların haberleşme yapılarının belirlenmesi.
- Confiğin son aşaması olan aygıtların/ sensörlerin birbirleri ile etkileşimlerini ve ona göre case event yapılarını inşasını ilk başta c test kodunda da yap. Daha sonra bunların test edilebilmesi için yapıları oluştur.

  ## Buradaki aşamanın gerçekleşmesi için adımlar.
    ### C aşamaları

  Bu aşamada amacımız sensörleri birden fazla fonksiyonu destekleyecek. Farklı yapılarda olabilecek şekilde. Her bir sensörün bir liste belirtebilecek şekilde inşa edilmesi gerekiyor. Sensörlerin ürettikleri veriler tek bir adres üzerinden yönetilebilmeli. Her oluşturulacak sensör çıktılarının typelarını belirtebilecek yapıların oluşturulması. Aynı şekilde inputlarında veri türlerinin belirlenebileceği yapıların hazırlanması gerekir.
   
  - Sensörleri/Aygıtlar oluştur. Bunu yaparken isimlendirebildiğinden emin ol. Sadece KNX RS485 ve Basic sensörlerin olduğunu varsay. Her bir sensör kendi içinde daha fazla sensör fonksiyon barındırabilmeli. Her birinin farklı türleri olabilmeli.
  - Bu sensör ve aygıtların oluşturulabilmesi aşamasını test et. Memory leak hiç bir şekilde kabul edilemez. Herhangi bir çökme herhangi bir şekilde kabul edilemez.
  - İlk başta sıralı işlemlerden oluşan bir yapı kur. Verileri bir txt den çek.
  - Daha sonra bir sürekli döngü kur. Birden fazla txt ile birden fazla kere sensör ekle farklı şekillerde ve sıralamalarda.
  - Artık veri değiştirme ve kontrol aşamalarının yapılması gerekir. Sıralı işlemeler ile sensör ekle. Sensör verilerini değiştir. Bir başka txt ile belirli bir süreli test yap. Memory leak kontrolleri yap.
  - Condition yapılarını yapmak için elimizde input verisi olarak belirldeğimiz türlere göre fonksiyonlar yaz. (istenilen değer (karşılaştırma durumu) elimizde olan değer = isimlendirlimiş durum / index)
  - Her bir sensörün verisinin birden fazla conditionu destekleyebilmesini sağla.
  - Conditionların out türlerini belirle ve isimlendir. (Mesala dijital veri türü için istenilen değere /eşit,altında üstünde) her bir sensör output ve input için tek tek belirlenecek ve isimlendirilecek.
  - ![Bu noktada yapı buna benziyor](https://github.com/sametyldrmm/OtelOtamasyonSistemDizayn/blob/main/images/diagram0.png)
  - Not kod yazmaya başlamadan önce ortaya çıkardığım yapıdır. Çok büyük bir değişiklik ortaya çıkmasada. Değişiklikler vardır. Son yapının hali düzenlendikten sonra atılacaktır. İlk planlamamdan oluşturduğum yapıyı yapay zekaya çizdirttim. Bunun bir database yapısı olduğunu düşündüğü için çizim üzerindeki işaretlere takılmayın. Genel yapı belli olabiliyor.
  - Conditionları txt den çekilecek şekille getir. Her bir sensör verisinde birden fazla olabilecek yada olmayacak şekilde çalışabilmeli.
  - Sensör oluştur. Condition oluştur. Conditionları sensörlere bağla. Condition outlarının güncellenen her bir veri için değişmesini sağla.
  - Şimdiki adımda farklı sensörlerin Conditionlarını bir birleri ile etkileşime sokacak yapıları yap. ( Zaten isimlendirmiştik isimler üzerinden ve/veya bağlaçlarını kullanan string üzerinden parse ederek bir değer oluştur) (uzaktan kontrol edilebilen if else yapılarına benzeyecek)
  - Sanal sensörler oluştur. Sanal sensör olduğunu belli eden Sanal Sensör tiplerine ekle. Buradaki yapı için her bir stringin belirlsiz karşıkları olabilmeli örnek olarak backendden temizlik=temizlik_yapıldı,temizlik_yapılmadı gibi sürekli değişen veriler gelebilir. Backkendden yeni bir SanalSensör oluştur isteği gelebilir. Uygun yapıları yap. Sanal sensörlerin conditiionları Backendden belirleneceko yüzden Sanal Condition verisi talep edebilecek yapıları kur.
  - Sanal Conditionları gerçek sensörlerin birbirleri etkileşime girmesini sağlayan yapıya koy ve etkileşime girmelerini sağla.
  - Genel test et.
  - Her bir sensör verisi için atadığımız condittionlar ve etkileşimini sağlayabildiğimiz yapıları tek bir yapıda birleştir. Her bir sensör verisi için oluşturulmuş Conditionları tek bir isim ile birleştir. ve bir değer oluştur.
  - Artık oluşturduğumuz Condition yapıları için eventleri belirlememiz gerekiyor. Bunu yapabilmek için boş fonksiyonlar oluşturmalıyız. İsimlerini kaydetmeliyiz. (Örnek (Log oluştur) fonksiyonunu yaptık. İsmini kaydettik. void * türünde veri alıyor. içerisinde cast ediyoruz. Bir ana fonksiyonda fonksiyon isimlerine göre doğru fonksiyona yönlendirme yapmalıyız. Dedikki en basit şekilde. Varlık sensörü için bir daha önce varlık sensörü bilgileri config aşama 1 2 3 te almıştık dp sinide biliyoruz. Sensör olarak dijital bir değer verdiğini varsayalaım. Txt lerimiz ile 0:eşit:varlıkSensörüNegatif , 1:eşit:varlıkSensörüPozitif, şeklinde Condition vermiştik. şimdide varlıkSensörüPozitif:"Log oluştur" u verdik eğer varlıkSensörüPozitif gerçekleşir ise log oluştur fonksiyonunu çalıştrıracağız. Burada varlıkSensörüPozitif_ve_SıcaklıkPozitif: log oluştur da denebilirdi bu seferde bu 2 Condition "ve" durumuna göre incelenerek log oluştur çalıştırılmalı )  Bu fonksiyonlar diğer sensörler/aygıtlara emir göndermek içinde kullanılacak. Hem oda içinde Backendden bağımsız işlemler. Hemde backende bağımlı işlemler içinde kullanılacak.

Bu aşamaların tamamı bittiğinde Config3 aşaması tamamlanmış olur. C tarafında Backend ile haberleşmeyi saymazsak ilk kurulması gereken yapı budur. Bundan sonrası burada txt ile yaptığımız her şeyin backend ile yapılması gerekir. Backend ile yapılırken dökümantasyonları oluşturacağız. Backendin buradaki configde ki görevleri en ince ayrıtnsına kadar yazılmalı. Bu yapıya göre Config 1,2,3 aşamlarıda yapılacak. O aşamalar Stm32 kodları içerisinde gerçkeleştirlecek. C test kodu görevi bitmiş olacak.
![](https://github.com/sametyldrmm/OtelOtamasyonSistemDizayn/blob/main/images/config3.jpeg)

Anlatılan mantıklarda base olarak alınan design paternler
## [Patterns in C Strategy](https://www.adamtornhill.com/Patterns%20in%20C%203,%20STRATEGY.pdf)
## [Design Patterns for State Machines ](https://repositorio.uci.cu/jspui/bitstream/123456789/10139/1/Design%20Patterns%20for%20Embedded%20Systems%20in%20C_%20An%20Embedded%20Software%20Engineering%20Toolkit%20%28%20PDFDrive%20%29.pdf)
İkinci Design Patterns for Embedded Systems isimli pdf'te Stm32 kodlar iken kullanabileceğimiz bir çok design pattern mevcut benim bu projede en çok ilgilendiğim kısım Design Patterns for State Machines kısmı olucak. Yukarıda anlattığım mantıkların test kodları bittikten sonra buradaki yapıların bizim sisteme uyarlanmış şekilleri ile devam edeceğiz. 

Basit bir şekilde anlatan bir dökümanı bırakıyorum. Direk bir şekilde patterni almak yerine isimleri fonksiyonlarla eşleştirip. Fonksiyon açıklamalarını ve hangi durumlarda kullanılabileceği gibi durumları backendde düzenleyerek. Her sensöre uyumlu çlışabilen kod blokları elde etmiş oluyoruz. Elde ettiğimiz yapı ile bir başka avantaj bir başka projede RPC yöntemi kullanılmak isterse direk bir şekilde uyumluluğu sağlanabiir

## Config 3 Aşaması Web Front
Web kurgusu üzerinden anlatım yapılacak. Frontend klosöründe bulabileceksiniz.
## Config 3 Aşaması Web NestJS
Java ile haberleşmesi için kullanılacak trigger yapılarından söz edilecek.
## Config 3 Aşaması JavaStm32Communaction
Hangi bilgileri nasıl bir yapı ile birleştirirerek gönderileceği anlatılacak.

Parça parça inşa
- JavaStm32Communication için dosya yapılarını belirle. İçleri boş dahi olsa. Tek tek classları oluştur. Hangi classın nereyle nasıl haberleşeceğini belirle. Env dosyaları gibi basit işlemleri yap. 
- Java için gerekli implemantasyonları yap. (server , dökümantasyon ,json vs)
- NestJs için gerekli implemantasyonları. (dökümantasyon , database vs) Env dosyaları gibi basit işlemleri yap. 
- NestJs için tahminen kullanılabilecek. Veritabanı şematiğini oluştur. Bunlar için CRUD ve filitre gibi temel yapıları oluştur. Aralarındaki ilişkileri oluştur.
- Java için ssl server oluştur. Serfikalarını oluştur. C için bir client oluştur ve bağlan.
- Stm32 lerde kullanılması planan Açık Anahtarlı Şifreleme ya uygun java ve c kodlarını yaz. Javaya bağlanmaya engel teşkil eden durumlarda bağlantıya izin verme.
- C test kodlarını inşa et.
- Java ile c test kodlarını C test kodlarındaki aşamalara uyarak haberleştir.
- Nestjs ile java yı socketleri kullanarak trigger yapılarını inşa et.Nestjs den gelecek bilgilere göre Java ile stm32 yi haberleştirecek yapıları yavaş yavaş inşa et.
     İlk yapılacak olan aşama.
  Stm32 lerin odalara bağlanabilmesini sağlayacak yapıları kurmak. Her bir stm32 bir odaya bağlı olup olmadığını belirtebilecek yapılara sahip olmalı. Eğer bağlanmaya engel olan bir yapı yok ise bir odaya bağlıysa bağlı olduğu odanın bilgilerini değilse ben bir odaya bağlı değilim bilgisin göndermeli. Java kodu kendi küçük databaseni kontrol etmeli ve bir odaya bağlı değil ise Nestjs e bir bildirim göndermeli. Nestjs gerekli yetkinliğe sahip kullanıcının bildirim paneline eklemeli. Basit bir fronttenden yada postmanden stm32 nin kurulu olduğu odanın bilgilerini göndermeli ve stm32 isimlendirmeli. Stm32 nin cevabını beklemeli Java ve kendi db sinde gerekli değişikliği yapmalı. 
- Postman ile Nestjs e verileri gönder. Oluşan database i yavaş yavaş doldur. Gelen bilgielere göre nestjs in java ile haberleşecek yapılarını kullan.

## C Test Back İlk Bağlantı
İlk bağlantı aşamasında ne gibi yapılar kullanılacak.

## İş Akışı / Sürec İş Planlama
Şimdiye kadar yapmış olduğum adım adım şekilde tüm sürecin (yapabildiğim kadarı ile)  yapabilabileceği şekilde adım adım progralamalarımı atacağım. Bir çok kısmını tek başıma test için inşa ettim çalışabilirliğinden emin olduğum kısımları atacağım.
Bu planlamalar gerçek işin günün sonunda olması gerektiği şekilde planlanmaya çalıştı. Benim test/çalışabilirlilik için yaptığım kodlardan bağımsız tekrar inşa edilecek.
Bunu burada değilde Direk iş akışı olarak adlandıracağım bir klosörde bulabileceksiniz.
Jira Yönetim sistemi üzerinden programlama yapmış idim.

## Klosör yapıların var oluş amaçları.
C dosya yapılarıda eklenecek.

## Sistem tasarımnın eksiklikleri
Network konusunda eksikliklerimiz çok fazla. Yukarıda bir başlık var fakat yüzeysel geçilmiş bir kısım.
Güvenlik önlemleri aldık fakat yeterliliği çok çelişkili bir durum.
Loglama konusu kesinlikle yetersiz. Hem planlama kısmı için hemde uygulama durumu ve kontrol mekanizmaları.

## Hiç bahsedilmemiş düşünülmemiş kısımlar.
Müşteri için en önemli olan Monitoring ve Reportlama kısımları. Çok fazla farklı yöntem ve sistem var. Bir çoğunun incelenip bir standartta karar verilmesi gerekiliyor.
Hazır açık kaynak sistemler üzerine inşa etmek daha mantıklı olabilir.
Sistem üzerindeki güç elektroniği. Bu kısım için bizim için bir sorun teşkil etmiyordu çünkü rework bir sistem yapacaktık . Bu sebeble bizim için bir sorun teşkil etmiyordu.


Vakit buldukça ekleme yapmaya devam edeceğim.
Bu şekilde aşırı karışık olduğunu düşündüğüm için klosörleme yaparak ilerleyeceğim. 

Projeyi muhtemelen çok uzun bir süre içerisinde bitirerek açık kaynak bir şekilde yayınlayacağım.

Şuanki süreçte tek başıma ilerlediğim için.
- Web arayüzü için [Havelsan Liman](https://liman.havelsan.com.tr/) sistemi üzerinden web kısımlarını halletmeye çalışacağım.  Çok yararlı Açık Kaynak bir projedir. İncelemenizi tavsiye ederim.
- STM32 üzerinde kurulması gerekilen yapı. C test kodları ve web arayüzü üzerinden temel işlemleri halletiktten sonra başlayacağım. Burada KNX gibi sensörlerin fiyatları çok yüksek olduğu için KNX daha sonraya kalacaktır. Başlangıçta standart sensörlerle , RS485 gibi hemen hemen her yerde kullanılan farklı haberleşme protokkellerini destekeyen farklı cihazları kullandıkça bir kütüphane mantığı gibi her cihazı web arayüzünden tamamen yönetibldiğimiz bir yapı kurmaya hedefleyeceğim.
  
## Havelsan Liman Sunucu Sistemi
Daha önce katıldığım Havelsan Açık Kaynak kampında görmüş ve öğrenmiş olduğum bir sistem. Çok sayıda avantajı olan süreçleri çok hızlandırabilecek bir sistem. Eklenti adı verdikleri yapılar var. Bu yapılar ile hemen hemen her işleminizi kolay bir şekilde halledebiliyorsunuz. Bu eklentileri geliştirmeyi kolaylaştırmak adınada bir çok APİ sağlamışlar. Kullanıcı işlemleri gibi bir çok güvenlik ve uğraş gerektiren kısmı basit bir şekilde panel üzerinden dahi halledebiliyorsunuz. Verilerinizi görselleştirmeyi ve üzerlerinde işlem yapmanızı sağlayan yapılarda mevcut. Ben web tarafında var olan zorlukları UI kötü bile olsa isteklerimi yerine getiren yapıları bu hazır sistem üzerinden inşa ederek prototip tarzı bir sistem geliştirmeyi hedefliyorum şimdilik. 

Çok daha detaylı bir şekilde sistemi analtan bir yazı hazırlayacağım.

