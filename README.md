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

Tüm bu config aşamaları adlandırılıp kaydedilebecek şekilde tasarlanacak. Bir odada beğendiğiniz bir configi istediğiniz odalara atayabilme.

## Sistem Tasarımı
- Tüm backend yapısı mikro servis mimarisi üzerine kurulu.
- Elektronikte planlanan haberleşme protokolleri. KNX RS485 I2C Bacnet Gateway

