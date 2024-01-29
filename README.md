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
5) Elektronik  Stm32 c

Sistemin frontend kısmındaki tasarımlarını burada yürüttüğüm mantık altında şekkillendiriyor olacağız.


### Başlıkların detaylandırılıp içlerinin doldurulması

## Frontend
Sadece kurgu çalışması yapıldı
Kurgu ile ilgili detaylar. Frontend klosörü içerisinde bulabilirsiniz.

## Bacnkend NestJS
```
1) device/
2) device-config-all-stm-modüle-partition/
3) device-config-basic/
4) device-config-knx/
5) device-config-rs485/
6) device-config-schematic/
7) device-config-schematic-room/
8) device-room/
9) env/
10) java-communication/
11) otel-config/
12) otel-config-bacnet/
13) room/
14) room-config/
15) room-guest/
16) room-log/
17) room-log-device/
18) room-staff/
19) typeorm/
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
[Murak Koca'nın Doktara tez çalışması]([https://www.google.com](https://tez.yok.gov.tr/UlusalTezMerkezi/TezGoster?key=RjZwH00oMG4iNa5Sgvlggz8LNOyM8hW0qnGPqs5nlNlSDJ9uEDbVwJwU2l8UYHpl))

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
Burada bahsedilen şematikerin amacı var olan aygıt sıralamasını öğrenerek isimlendirmesini yapılabilmesi bunu yaparak daha sonradan her odaya özgü tasarımlar yapabilir. Normal aygıtlar için hangi pine bağlanabileceklerini oteldeki kurulumu yapan kişiye bildirilmesi. KNX ve RS485 hatları için fiziksek adres gibi özelliklerin stm32 içerisinde doğru bir şekilde configüre edilebilmesini sağlanabilmesi. Web arayüzü üzerinden hiç otelde bulunmadan. Gerekli düzenlemelerin yapılabilmesinin sağlanabilmesii. İlk kurulum için işleri hızlandırma ve 900 odalı oteller gibi yerler için kullanılabilir bir sistem tasarlamayı mümkün hale getirmesi. İlk kurulumdan sonraki süreçte istenildiği anda ek cihaz eklenip cihaz devre dışı bırakılabilmesinin sağlanabilmesi.
4) Her odaya özgü istenilen yetkinliklerin kazandıralabilmesi amaçlı zaman config ayarlaması.
   - Örnek olarak odada bulunan ışıkların müşteri varken ve yokken gibi durumlar ile birlikte zaman ayarlamarının yapılabilmesi. (müşteri odadan çıktıktan 10 dakika sonra açık ışıkları kapatmak)
   - Klima, perde vs tüm cihazlar için tek tek zaman ayarlamaları.

Burada bahsedilmesi gerekilen bir başka staratereji.
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
Bu aşamaya kadar elimizde olan sensörlerin oluşturacağı durumları Bool değerler olarak Map yapısına benzer şekilde alabiliyoruz.
Bu noktada başka bir ihtiyaç doğuyor. Sürekli bir şekilde almadığım verilerin condititonlarına ihtiyaç duyuyor oluşum.
Mesala bir özel müşterinin yada otelde çalışan elemanların bir işlemin condititonlarımı etkilemesi gerekliliği. Örnek temizlik mesajı personele iletildi ama temizlik yapılmadı. Bu durum benim sensörlere emir gönderirken dikkat etmem gereken bir özel durum oluşturabilir.

Bunuda Sanal Sensör adını verdiğim yapılar sayesinde yapacağız.
İlk başta boşta duran fonksiyonlardan söz etmiştik. 
Burada backenden bilgi talep et gibi özel bir fonksiyon olabilir. 
Belirlenmiş string karşılıkları ile her özel duruma karşı bir bool değerin 
Stm32 içerisindeki kodu değiştirmeden alınıp doğru bir şekilde işlenebilmesi.

Örnek:
"Bool:temizlikPozitif,TemizlikNegatif:Temizlik_durum", olarak stm32 ye iletildiğnide stm32 nin burada olan bilgileri Dp sine göre Temizlik_durum ile eşleştirmesi.

ve bunu bir sensör gibi kendi içinde kaydetmesi. Daha sonra aynı başlıktan bir bilgi talep edebilir ve bir bilgi gönderebilir konumda olmuş olacak.

Bu aşamalar başarılı şekilde yapıldıktan sonra oluşturduğumuz condititionların kendileride dahil olmak üzere diğer sensörleri aygıtları etkileyebilmesini sağlamak.

Bu aşama için yapılması gerekilenler.
- VarlıkSensörüPozitif 

Bu aşama içinde daha önceden belirlenmiş stm32 içerisinde tanımlamış olmamız ve bunları alacakları parametreleri ile databasemize kaydetmemiz gerekir.

Örnek fonksiyon örneği.
- Loger fonksiyonu. Alacağı parametreler. (char *)
    Yapacağı iş 

### **Burada bahsedilen Config STM32 straterejisi nin çalışabilrliği test edilmiş ve çalışan bir algoritma ortaya konulmuştur. Ekonmoik kaygılardan dolayı paylaşılmayacaktır. C kodu olarak test edilmiş. STM32 ye geçirlilmemiştir. STM32 ye uyarlanabilecek şekilde düşünülerek kod'lar yazılmıştır**

Tüm bu config aşamaları adlandırılıp kaydedilebecek şekilde tasarlanacak. Bir odada beğendiğiniz bir configi istediğiniz odalara atayabilme.

## Sistem Tasarımı
- Tüm backend yapısı mikro servis mimarisi üzerine kurulu.
- Elektronikte planlanan haberleşme protokolleri. KNX RS485 I2C Bacnet Gateway

