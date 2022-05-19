---
title: VirtualBox'a Linux Kurulumu (Pardus)
date: 2010-01-12 02:24
---

Linux'a iyiden iyiye merak sardım bu aralar. Önce hangi dağıtımı seçeceğime karar vermek için, daha sonra da bozdukça bir daha bir daha gerektiği için onlarca kez Linux kurulumu yaptım 🙂 Şu an bu yazıyı yerli dağıtımımız Pardus'tan gönderiyorum 🙂

<!--more-->
Gelelim bu yazının da konusuna. Denemek isteyip deneyemeyenler için, Linux'a nereden başlayacağını bilemeyenler için, hiç ilgisi olmamasına rağmen dünya gözüyle Linux'u da bir göreyim diyenler için bir sanal bilgisayar oluşturup, yerli dağıtımımız Pardus'u bu bilgisayara yükleyelim hep beraber 🙂 Kullandıkça Windows'a çok güzel bir alternatif olduğunu düşünmeye başladığım Linux serüvenine sizleri de davet etmiş ve elinizden tutmuş olayım...

Yukarıda dediğim gibi, kurulumu bir "***sanal bilgisayar***" üzerine yapacağız. Bu sanal bilgisayarı da Microsoft'un *Virtual PC* adlı programıyla ya da Sun'ın *VirtualBox* programıyla oluşturacağız. Ben bu yazıda VirtualBox adlı programı kullanacağım ve yaptığım işlemlerin ekran görüntülerini tek tek sizlere sunacağım.

Yine ilk kez deneyecek arkadaşlara belirteyim, mevcut işletim sisteminiz bu kurulumdan hiçbir zarar görmeyecek. Windows'unuz altında çalışan bir Linux'a sahip olacaksınız ve gerçek bir bilgisayara kurduğunuzda çalışacağı gibi çalışan (hemen hemen) bir işletim sisteminiz daha olacak. Yani bu yeni işletim sisteminizi Windows'un içindeki herhangi bir programı çalıştırır gibi çalıştıracaksınız.

Şimdi gelelim VirtualBox adlı programı edinmeye. [Bu adresteki](http://www.virtualbox.org/wiki/Downloads)  ilgili bağlantıdan programı indiriyorsunuz. Ben bu yazıyı yazarkenki en güncel sürümü 3.1.2, 5 dakika içinde indi. İndirdiğimiz dosyayı çalıştırıp, gerekli adımları geçip kurulumumuzu bitiriyoruz.

![VirtualBox_1](/uploads/2010/01/VirtualBox_1.png)

![VirtualBox_2](/uploads/2010/01/VirtualBox_2.png)

Kurulum bitince masaüstümüze yerleşen VirtualBox kısayoluna tıklayıp programımızı çalıştırıyoruz. İlk açılışta kayıt ekranı gelebilir. Bunu geçebiliriz bir mahsuru yok.

![VirtualBox_3](/uploads/2010/01/VirtualBox_3.png)

Programın ekran görüntüsünden de anlayacağınız üzere, (kısmen de olsa) ***Türkçe***'ye çevrilmiş bir program ve nerede ne yapabileceğimizi kestirebileceğiz. İngilizce bilmeyen arkadaşlar açısından bir kolaylık olacaktır. Şimdi sanal bilgisayarımızı oluşturmak için "**Yeni**" butonuna tıklayalım.

![VirtualBox_4](/uploads/2010/01/VirtualBox_4.png)

Gördüğünüz gibi "***Sanal Makine Oluşturma Sihirbazı***" başladı. İleriye basınca, sanal bilgisayarımız için bir isim girmemizi ve hangi işletim sistemini yükleyeceğimizi soracak.

![VirtualBox_5](/uploads/2010/01/VirtualBox_5.png)

Yukarıdaki resimde de gördüğünüz üzere "***Linux***" işletim sistemi yükleyeceğimizi belirttik. Eğer Pardus'tan farklı bir dağıtım kurmak isterseniz ve "***Version***" listesinde varsa seçebilirsiniz. Pardus, seçeneklerde olmadığı için "***Other Linux***" seçip devam ediyoruz.

![VirtualBox_6](/uploads/2010/01/VirtualBox_6.png)

Karşımıza yukarıda gördüğünüz "***Bellek***" adımı geliyor. Sanal bilgisayarınız için bellek miktarını burada belirleyeceksiniz. Varsayılan rakam olan **256MB**, Pardus için çok yetersiz olacaktır. Bu yüzden elinizden geldiği kadar yüksek RAM ayırmanız, çalışmanızda size kolaylık sağlayacaktır. Ben bu kurulum için ***1024MB*** bellek ayırdım. Yeterlidir...

**NOT:** Ayırdığınız bellek miktarı sanal bilgisayar tarafından kullanılacağı için fazla uçmamanızda fayda var. Şöyle ki **2GB** belleği olan ***Windows 7*** işletim sistemi çalışan bilgisayarımda oluşturduğum sanal bilgisayara **1500MB** bellek ayırırsam, kalan **548MB** kısım Windows için yeterli olmayacağından aşırı *yavaşlama* söz konusu olacaktır. Hala çalışmaya devam edecek Windows'u da göz önünde bulundurup makul bir miktar ayırmanız her iki işletim sisteminin de rahat çalışması açısından önemli.

![VirtualBox_7](/uploads/2010/01/VirtualBox_7.png)

Belleğimizi ayırdıktan sonra geriye bir de sabit diskimiz kalıyor. Bunun için de yukarıda gördüğünüz gibi yeni bir birincil sabit disk oluşturmak için "***Create new hard disk***" seçip ilerliyoruz.

Sabit disk oluşturma sihirbazı sırayla depolama tipi, diskin konumu ve boyutunu soracak. Ekran görüntüsüne gerek duymuyorum sadece seçtiklerimi söyleyeyim. Depolama tipi olarak "***Dinamik olarak genişleyen kalıp***" seçebilirsiniz. Böylece ilk etapta bilgisayarınızdaki disk üzerinden küçük bir parça ayrılır, kullanım esnasında gerektikçe diskinizden kullanılır. Konum ve boyut bilgilerine gelirsek bu adımda değişiklik yapmanıza gerek yok. Varsayılan değer olan **8GB** disk alanı Pardus için yeterlidir. Bu bilgileri girdikten sonra "***Bitir***" ile sabit diskimizi de oluşturmuş oluyoruz.

![VirtualBox_8](/uploads/2010/01/VirtualBox_8.png)

Sanal bilgisayarımızı oluşturmadaki son aşama olarak, seçtiğimiz özelliklerin özetini görüyor ve sanal bilgisayarımızı kullanıma hazır hale getiriyoruz.

![VirtualBox_9](/uploads/2010/01/VirtualBox_9.png)

İşte bilgisayarımız kullanıma hazır. Sadece Pardus'u bu bilgisayara kurmak kaldı. O iş de çocuk oyuncağı 😉 Eğer hala edinmemişsek [bu adresten](ftp://ftp.pardus.org.tr/pub/pardus/kurulan/2009/Pardus_2009.iso) CD kalıbını indiriyoruz. Oluşturduğumuz bilgisayarı bu CD ile başlatıp kurulum adımlarına geçeceğiz. Şimdi programımızda Pardus2009 adlı bilgisayarı seçip Başlat diyoruz. Aşağıdaki resimde gördüğünüz yere gidip CD kalıbımızı sanal bilgisayarımızın sürücüsüne takacağız.

![VirtualBox_10](/uploads/2010/01/VirtualBox_10.png)

Sanal Ortam Yöneticisi ekranında "***Ekle***" deyip, indirdiğimiz iso dosyasını seçiyoruz. Kurulum CD'sini bilgisayarımıza taktığımıza göre tek yapmamız gereken bilgisayarı bu CD'den başlatmak. Onun için de "***Makine***" menüsünden "***Sıfırla***" seçebilir, ya da kapatıp tekrar başlatabilirsiniz.

Yeniden başlattığımızda bilgisayar CD'mizden başlayacak ve aşağıdaki ekran sizi karşılayacak.

![Pardus_1](/uploads/2010/01/Pardus_1.png)

Pardus 2009'u seçip Enter tuşuna basıyor ve kurulumu başlatıyoruz.

![Pardus_2](/uploads/2010/01/Pardus_2.png)

Lisansı kabul edip ilerliyoruz. Bir sonraki adımda CD'mizin doğruluğunu kontrol ediyoruz. Etmeyebiliriz ama etmekte fayda var. Sonraki adımlar sırayla klavye ayarımızı, zaman dilimimizi, kullanıcı adı ve parolamızı, sistem yöneticisi parolamızı (sistem ayarlarını yaparken ister), yükleyeceğimiz diski soracak. Kullanıcı adı ve parola belirlemek dışında bir ayar yapmanıza zaten gerek kalmıyor.

![Pardus_3](/uploads/2010/01/Pardus_3.png)

Ve artık kuruluma başlıyoruz.

![Pardus_4](/uploads/2010/01/Pardus_4.png)

Kurulum tamamlanıncaya kadar Pardus hakkında genel bilgiler veriliyor. Arkanıza yaslanıp bu bilgileri okuyabilir, ya da gidip başka bir işinizi halledebilirsiniz. Çünkü yukarıda yazdığı gibi 20 dakikada bitmiyor kurulum (sanal bilgisayarda).

Kurulum arkaplanda süredursun, ben de size VirtualBox hakkında küçük birkaç bilgi daha vereyim.

![VirtualBox_11](/uploads/2010/01/VirtualBox_11.png)

VirtualBox penceresinin altındaki bu ikonlar nedir, ne işe yarıyor, bize ne gösteriyor?

İlk sıradaki sabit diskimizi temsil ediyor. Üzerinde kırmızı ışık yanınca diskimize bilgi kaydediyor, yeşil ışık yanınca okuyor. İkincisi CD sürücümüz, yine aynı şekilde bilgi okuduğuna dair bir yeşil nokta var üzerinde. Üçüncüsü ağ bağlantısını, sonraki takılan USB aygıtlarını, sonraki paylaşılan klasörleri gösteriyor. "Right Control" ise içlerinde en çok işimize yarayanı. Bu işletim sistemini kullanırken faremizle ekrana tıkladığımızda, giriş aygıtlarımızı sanal bilgisayar alır, ve sadece o ekranda kullanabiliriz. Windows'a geri dönmek ve giriş aygıtlarımızı o pencereden ayırmak için "***Sağ Ctrl***" tuşuna basacağız.

Bu arada o da ne? Pardus'umuz kurulmuş 🙂

![Pardus_5](/uploads/2010/01/Pardus_5.png)

Artık Pardus'u tecrübe etmemize bir arpa boyu yol kalmış. İleri deyip, sistemi yeniden başlatıyoruz.

![Pardus_6](/uploads/2010/01/Pardus_6.png)

Bu aşamada herşey tamalandı, Pardus gül cemalini göstermek için bizleri bekliyor 🙂 Bu uğurda aşmamız gereken tek engel ise kurulumda belirlediğimiz kullanıcı adımızı ve parolamızı girmek 🙂

![Pardus_7](/uploads/2010/01/Pardus_7.png)

Bilgilerimizi girip oturum açtığımızda Pardus bizi güzel masaüstü ortamıyla karşılıyor. İlk açılışta, birkaç ayarı yapmak için Kaptan sizi bekliyor olacak (masaüstü arkaplanı, ağ bağlantısı vb. ayarlar).

![Pardus_8](/uploads/2010/01/Pardus_8.png)

İşte Pardus 2009'un masaüstü. Takdir edersiniz oldukça hoş bir görünümü var. Denerseniz göreceksiniz ki çok kullanışlı menüleri var, herşeye rahatça ulaşabiliyorsunuz.

Çok kısa sayılabilecek bir süredir Linux ile içiçe olduğum halde gördüm ki, program bulma açısından Windows'u aratmayacak kadar geniş bir yazılım yelpazesi var Linux'un da. Pardus ise ihtiyacınız olacak hemen hemen herşeyi zaten içinde barındırıyor (müzik ve video çalar, internet tarayıcısı olarak Firefox, anlık mesajlaşma uygulaması, ofis paketi ve aklınıza gelebilecek diğer herşey). Barındırmadığı ihtiyaçlarınızı ise küçücük bir Google aramasından sonra keşfedip yükleyebiliyorsunuz. Demem o ki, eğer bilgisayarınızı oyun oynamak için kullanmayacaksanız Linux çok güzel bir alternatif, ve yerli dağıtımımız Pardus tercih edilmesi gereken bir işletim sistemi. (Oyunu yine hariç tutarsak) Windows ile yapabildiğiniz herşeyi Linux ile yapabiliyorken neden 213 TL lisans parası ödeyesiniz? (213 TL, Vatan Bilgisayar'ın Windows 7 Home Premium fiyatı) Bu son cümle hakkında Yavuz arkadaşımız [şunları](http://www.turkcejava.com/index.php/ev-kullanicilari-icin-neden-linux) yazmıştı, belki göz atmak istersiniz...

Konuyu bir Windows-Linux tartışmasına dönüştürmeden toplayayım isterseniz 🙂 Şimdi bakınca oldukça uzattığımı gördüğüm bu yazıda asıl amaç VirtualBox ile bir sanal bilgisayar oluşturup, Linux kurulumu yapmaktı. Başardık, mutluyuz 🙂

Pardus olması şart değil, bu vesile ile belki siz de Linux'a merhaba diyeceksiniz. Benden tavsiye isterseniz Ubuntu da kurabilirsiniz derim (ki kullanıyorum, memnunum). Peki Ubuntu tavsiye ederken neden Pardus kurdum? Çünkü Pardus'tan da memnunum, gelişmesini ve yaygınlaşmasını istiyor ve onu da tavsiye ediyorum 🙂

Herneyse, artık bitireyim...  
Sanal bilgisayarınız ve yeni işletim sisteminiz hayırlı olsun efendim.  
Deneyin, kesinlikle memnun kalacaksınız...  
Sevgiler...
