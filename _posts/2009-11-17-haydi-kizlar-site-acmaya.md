---
title: Haydi Kızlar Site Açmaya 🙂
date: 2009-11-17 23:59
---

Bana en çok sorulan sorulardan birisi bu: "***Nasıl site yapabilirim?***" Bu yazımda da bu soruya bir cevap vermiş olayım ve adım adım sizlerle bir site oluştup kullanıma hazır hale getirelim.

![haydisiteacmaya](/uploads/2009/11/haydisiteacmaya.gif)  

<!--more-->
Bir site açabilmek için nelere ihtiyacımız var önce bu soruların cevabını verelim. Sitenizin dosyalarını barındırmak için bir web sunucusuna (bunun için *hosting* hizmeti satın alırız) ve bir alan adına (*domain*) ihtiyaç duyarsınız. Temelde bu ikisi web siteniz için olmazsa olmazdır. Ancak merak etmeyin, bu yazının sonuna ulaştığınızda hiç para harcamadan, kendi bilgisayarınızı bir web sunucusuna dönüştürüp sitenizi oluşturmuş olacaksınız 😉

Diğer bir ayrımı da burada yapmak istiyorum: Web sitesi yapmak ve web sitesi açmak birbirinden farklı şeylerdir. Herkes site açabilir, ama web sitesini oluşturmak; kodlama, tasarım gibi zahmetli bir süreci gerektirir. Biz burada hazır yazılımlar kullanarak kendimize bir site açmış olacağız, site yapmış değil 🙂

Artık yavaş yavaş başlayalım. Önce ihtiyaçlarınızı belirlemelisiniz. "***Neden site açmak zorunda hissediyorsunuz?***" sorusuna cevap vermeniz lazım. Bu sorunun cevabı "*Bir topluluk oluşturacağım.*" olduğu zaman bir forum yazılımı (MyBB, vBulletin gibi), "*Kişisel yazılarımı paylaşacağım.*" olduğu zaman bir blog (web günlüğü) yazılımı (Wordpress gibi), "*Ürünlerimi satacağım.*" olduğu zaman bir alışveriş yazılımı (osCommerce gibi) olacaktır. İhtiyaçlarınıza göre bu yazılımlardan birini seçmeniz gerekir (çünkü dediğimiz gibi site yazmayacağız, yazılmış olanları alıp site açacağız). "*Ne tür siteler var? Hangileri nasıl nerden bilip de tercih edeceğim?*" sorularının cevabını da [Open Source CMS](http://php.opensourcecms.com) web sitesine göz atarak bulabilirsiniz. Buradan tüm bu sitelerin nasıl çalıştığını deneyip karar verebilirsiniz.

Ben bu yazımda, bu sitenin de altyapısını oluşturan *Wordpress* ile site oluşturmayı anlatacak olsam da, diğer tüm yazılımlar da benzer şekilde kurulup, benzer şekilde çalıştığı için siz istediğinizi kolayca kendi oluşturacağınız siteye uygulayabilirsiniz.

Yukarıda belirtmiştim. Web sitemizin dosyalarını barındırmak için bir web sunucusuna ve alan adına ihtiyacımız var. Bu ihtiyacı bizler için çözecek olan programın adı "***EasyPHP***". Bu program içinde *PHP* kodlarını çalıştıracak programı, *Apache web server* ve *MySQL* veritabanı sunucusunu barındırıyor. Bu sayede PHP ile kodlanmış yazılımları çalıştırabilecek, sitemizin kullanması için MySQL veritabanı oluşturabilecek ve sitemizi bir web tarayıcısı ile görüntüleyebileceğiz. Belirtmedim, zamanı geçmeden belirteyim: PHP ile yazılmış ve MySQL veritabanı kullanan sistemleri bu şekilde kurabiliyorsunuz. ASP veya diğer dillerle yazılmış uygulamalar için bu anlattıklarım geçerli olmayacaktır. "*Seçtiğim yazılımın PHP ve MySQL kullandığını nereden öğreneceğim?*" sorusunun cevabını da sitenize kurmak istediğiniz sistemin web sayfasında bulabilirsiniz.

Şimdi EasyPHP'yi kuralım ve web sunucumuzu kullanıma hazır hale getirelim. EasyPHP'nin ben bu yazıyı yazarkenki son sürümü *EasyPHP 5.3.0*'ı [buraya](http://sourceforge.net/projects/quickeasyphp/files/EasyPHP/5.3.0/EasyPHP-5.3.0-setup.exe/download) tıklayıp indirebilirsiniz. Kurulum ekranı aşağıdaki gibidir:

![easyphp_1](/uploads/2009/11/easyphp_1.gif)

Buradan English seçelim ve Tamam'a tıklayıp devam edelim. Biliyorsanız diğer dillerden de seçebilirsiniz tabi 🙂

Aşağıdaki gibi bir görüntü ile karşılaşacaksınız. "Next" butonuna tıklayalım. Bir sonraki adımda kullanıcı sözleşmesini kabul etmenizi isteyecek, onu da kabul edip kurulum bitene kadar "Next" butonuna tıklayın.

![easyphp_2](/uploads/2009/11/easyphp_2.gif)

Ve kurulum bitince görev çubuğunda EasyPHP'nin simgesi belirecek.

![easyphp_3](/uploads/2009/11/easyphp_3.gif)

Bu aşamada, bahsettiğimiz alan adı, web sunucusu işlemini halletmiş olduk. Apache web server bilgisayarınıza kuruldu, PHP dosyaları çalıştırılabilir durumda ve artık bir adresiniz var: **http://localhost** ya da **http://127.0.0.1** Bir not olarak şunu da eklemek istiyorum. *Bu adreslere sadece bilgisayarınızdan ulaşılabilir*. Sitenizi internette değil kendi bilgisayarınızda yayınlayacaksınız. Amaç bilgisayarımızı internete açıp, altından kalkamayacağımız işlerin altına girmek değil, sadece öğrenmek 😉

Daha önceden ihtiyaçlarımızı sorgulamış ve bu ihtiyacın kişisel bir site olduğuna karar vermiş, bunun için de Wordpress kullanmayı uygun görmüştük. Şimdi hemen Wordpress'in son sürümünü edinelim ve sitemizi kurmaya başlayalım. Wordpress'in Türkçe son sürümünü indirmek için [bu](http://www.wordpress-tr.com/?file_id=2) bağlantıyı tıklayabilirsiniz. Bende İngilizce sürümü vardı onun üzerinden anlatacağım, ama aynı pencereler olduğu için Türkçesini sorunsuz kurabileceksiniz. Sadece yazdıklarımı okumaya ve ekran görüntülerini takip etmeye devam edin.

Wordpress'i indirdik. İndirdiğimiz ZIP dosyasını açıyoruz ve içindeki "***wordpress***" adındaki klasörü görüyoruz. Bu klasörün içindeki tüm dosyaları -aşağıdaki resimde de gördüğünüz gibi- şu klasöre kopyalıyoruz: ***C:/Program Files/EasyPHP5.3.0/www***. Bu klasör bizim yayın klasörümüz oluyor. Buraya attığımız her dosya yerel web sitemizde görünebiliyor.

![easyphp_4](/uploads/2009/11/easyphp_4.gif)

Ve dosyalarımızı kopyaladık. Sitemizi kurmaya başlamadan önce tek bir adım kaldı: **Veritabanı oluşturmak**. Evet, bundan daha önce de bahsetmiştik, sitelerimizin çalışması için bir veritabanına ihtiyacımız var. Bu işi yapmak için de "***phpmyadmin***" adlı programı kullanacağız. Ulaşmak için web tarayıcınızın adres çubuğuna şunu yazmanız gerekiyor: ***http://localhost/home/mysql/*** . Şimdi phpmyadmin'i kullanıp kendimize bir veritabanı oluşturacağız. Bunun için aşağıda gördüğünüz gibi veritabanımıza bir isim verip "***Oluştur***" butonuna tıklıyoruz.

![phpmyadmin_1](/uploads/2009/11/phpmyadmin_1.gif)

Oradaki diğer seçeneklerin ne olduğunu bilmenize şimdilik gerek yok 🙂 Sadece isim verip oluşturalım. Ve işte veritabanımız oluşturuldu.

![phpmyadmin_2](/uploads/2009/11/phpmyadmin_2.gif)

Artık Wordpress kurulumuna geçebiliriz. Kuruluma geçmek için yayın klasörümüz olan ***www*** içindeki dosyalara ulaşmalıyız. Ona ne şekilde ulaşıyorduk hatırlayalım: Adresimiz ***http://localhost*** ile. Bu adrese gittiğimizde Wordpress kurulumu otomatik olarak başlayacak. Aşağıdaki ekranda da gördüğünüz gibi konfigürasyon dosyanız olmadığına ilişkin bir uyarı ile kurulum işlemine başlıyoruz.

![wp_1](/uploads/2009/11/wp_1.gif)

"*Create a Configuration File*" ya da Türkçe sürümde "*Konfigürasyon dosyası oluştur*" butonuna tıklayıp devam ediyoruz. Bir sonraki adımda (resmi aşağıda görüyorsunuz) bu konfigürasyon dosyasında hangi bilgilerin bulunacağını görüyoruz.

![wp_2](/uploads/2009/11/wp_2.gif)

"*Let's Go*" ya da yerindeki Türkçe butona tıklayıp bir sonraki adımda sitemizi kurmamız için gereken veritabanı bilgilerini giriyoruz.

![wp_3](/uploads/2009/11/wp_3.gif)

"*Database Name*" yani "*Veritabanı Adı*", phpmyadmin'de oluşturduğumuz veritabanının aynısı olmalı ki Wordpress buraya ulaşıp gerekli bilgileri kaydedebilsin. "*User Name*" yani "*Kullanıcı Adı*" veritabanına ulaşmak için kullanacağınız isimdir. Localhostta çalışırken bu isim "***root***" olacak ve veritabanı parolası yani "*Password*" **boş bırakılacak**tır. Resimde gördüğünüz "*Table Prefix*" alanında herhangi bir değişiklik yapmıyoruz. Ne işe yaradığını merak edenler için söyleyeyim: Veritabanında oluşturulan tabloların isimlerinin başına bu ön ek getirilecek (wp_authors gibi).

![wp_4](/uploads/2009/11/wp_4.gif)

Yukarıda gördüğünüz gibi, Wordpress için gereken tüm bilgileri girdik, kuruluma başlama ve veritabanı tablolarını oluşturma zamanı geldi. "*Run the install*" ya da "*Kuruluma Geç*" butonuna tıklıyoruz ve sitemiz için gereken son bilgiyi veriyoruz.

![wp_5](/uploads/2009/11/wp_5.gif)

Sitemizin başlığını buradan seçiyoruz (Şu an tarayıcının sol üstünde görüyorsunuz *Hasan Gök | Karalama Defteri* şeklinde. Başlık dediğimiz yer orası oluyor ve adı üstünde sitenizin başlığı oluyor 🙂) ve mail adresimizi de yazıp "*Install Wordpress*" ya da  Türkçesi "*Wordpress'i Kur*" butonuna tıklıyoruz.

![wp_6](/uploads/2009/11/wp_6.gif)

Ve sitemizin kurulumunu tamamladık, sitemiz artık kullanıma hazır. Yukarıdaki ekran yönetici paneline girişimiz için gerekecek kullanıcı adını ve şifreyi bize söylüyor. Bu kullanıcı adı her zaman admin olsa da şifre rastgele oluşturulur. O yüzden dikkatlice kopyalayıp, panele girdiğinizde ilk iş onu değiştirmeniz yararınıza olacaktır. Şimdi "*Log in*" ya da "*Oturum Aç*" butonuna tıklayarak aşağıdaki ekranda gördüğünüz gibi kullanıcı bilgilerimizi giriyoruz.

![wp_7](/uploads/2009/11/wp_7.gif)

Vee Wordpress'in site yönetim ekranı karşınızda.

![wp_8](/uploads/2009/11/wp_8.gif)

Wordpress sitemizi başarıyla kurduk arkadaşlar. Bundan sonrası size kalmış. Peki bundan sonrasında ne yapacaksınız? Sitenize içerik ekleyecek, görüntüsünü değiştirecek, yeni sayfalar oluşturacaksınız. Bunları nasıl yapacağınızı ben anlatmayacağım. Neden? Çünkü son ekran görüntüsünde de gördüğünüz gibi her şey yerli yerinde ve siz bu işlemleri kolaylıkla yapabilirsiniz. Örneğin yazı eklemek için "*Posts*" yani "*Yazılar*" kısmından "*Add new*" ya da "*Yeni Ekle*" bağlantısına tıklayıp yazınızı yazacaksınız. Tıpkı Word'de yazı yazar gibi 🙂 Ya da yeni bir sayfa eklemek için "*Sayfalar*" bölümünü, sitenizin görüntüsünü değiştirmek için "*Görünüm*" bölümünü kullanacaksınız. İşte bu kadar basit.

"*Bu kadar zahmete sadece kendi ulaşabileceğim bir site için mi katlandım?*" diye düşünen arkadaş çıkmaz biliyorum ama yine de cevaplayayım her ihtimali göz önünde bulundurup 🙂 Bir siteyi internette yayınlamadan önce kendi bilgisayarınıza kurup, kurduğunuz sistemi iyice tanımak, gerekli düzenlemeleri yapmak, hataları gidermek gerekir (en azından ben böyle yapıyorum). Eksik, düzensiz bir siteyi yayınlamaktansa düzeltilmesi gerekenleri kapalı kapılar ardında yapıp, en temiz en güzel halini ziyaretçilere sunmak gerekir. Her neyse. Şimdilik tek amacımız öğrenmekti zaten. Belki ilerleyen zamanlarda internette bu işlerin nasıl yapıldığını anlatan bir yazı da yazarım 🙂

Yazı oldukça uzun olmuş şimdi fark ettim ama sıkılmamışsınızdır okurken eminim 🙂  
Yeni siteniz hayırlı olsun arkadaşlar, güle güle kullanın, güle güle öğrenin...
