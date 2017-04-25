---
layout: post
title: SharePoint-Hosted Apps - Ortam Hazırlıkları
date: 2013-12-20 00:19
author: hasangok
comments: true
Tags: [SharePoint, Sharepoint 2013, SharePoint Management Shell, SharePoint-Hosted App]
---
![Sharepoint-2013-Logo](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/Sharepoint-2013-Logo.png)
Uzun zamandır bu yazıyı yazmak istiyorum belki birinin işine yarar düşüncesiyle. Bundan birkaç ay öncesinde benden örnek bir uygulama (yazının devamında uygulama diye bahsettiğim, *SharePoint-Hosted App*'in kendisi olacak) geliştirmem istendiğinde, çetrefilli bir işin ortasında buldum kendimi. Şu an baktığımda, en azından geliştirme ortamını hazırlama işleminin o kadar da zor olmadığını düşünsem de, yeni başlayacak arkadaşların kafalarında oluşan soru işaretlerini bir nebze de olsa giderip, ilk uygulamalarını geliştirmelerinde yardımcı olabileceğimi umuyorum. Piyasada konuyla alakalı yüzlerce makale olsa da, ben elde ettiğim sonuçların özeti ve hazırlıkları tamamlamanın en kısa yolu niteliğinde bu yazıyı sizlerle paylaşmak istedim. Neyse, uzun cümleler kurmaktansa adım adım işlemlerimize geçelim.
**Adım 1:** Bilmemiz gereken ilk şey, *SharePoint 2013* üzerinde uygulama geliştirebilmek için, iki servisin çalışıyor olması gerekiyor. Bunlar:

1. App Management Service
2. Microsoft Sharepoint Foundation Subscription Settings Service

![sp2013-services-on-server](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/sp2013-services-on-server.png)

Bu iki servisin çalıştığını teyit etmek ve çalışmıyorsa başlatmak için *Central Administration* sayfasından *Manage services on server* linkine tıklayıp, ilgili servisleri başlatabilir / çalıştığını teyit edebiliriz.

**Adım 2:** *Sistem hesabı* kullanıcısıyla uygulama geliştirmesi yapamıyoruz. Bu yüzden uygulama geliştirebilmek için kendimize bir kullanıcı oluşturmamız gerekiyor. İstediğiniz ismi seçmekte özgür olmakla beraber ben bu kullanıcıyı ***SpAppAdm*** adıyla oluşturacağım. *Active Directory Users and Computers* kullanarak aşağıdaki ekran görüntülerinde gördüğünüz gibi yeni bir kullanıcı oluşturabilirsiniz.
![ad-new-user-1](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/ad-new-user-1.png)
![ad-new-user-2](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/ad-new-user-2.png)

Burada önemli gördüğüm birkaç noktaya değinmek istiyorum:

1. *Active Directory*'de oluşturduğunuz bu kullanıcıyı bir sonraki adımda (ve daha sonralarda) kullanabilmek için *User Profile Synchronization* başlatmamız gerekiyor. *SharePoint 2013*'ün *Foundation* sürümü için böyle bir özellik olmadığından senkronizasyon işlemine de gerek kalmıyor.
2. Kullanıcımız geliştirdiği uygulamaları deploy edeceğinden, *SharePoint* veritabanında gerekli yetkileri tanımlamamız gerekiyor. Bunun için *SQL Server Management Studio* ile veritabanı sunucusuna bağlanıp *Security* &gt; *Logins* &gt; *New Login* yolunu izleyerek *Server Roles* sekmesinden en azından *dbcreator*, *public* ve *securityadmin* seçeneklerini işaretlememiz gerekiyor.
3. Uygulamaları çalıştırırken herhangi bir sıkıntı yaşanmaması adına, kullanıcımızın *Local Admin* (yerel yönetici) hesabı olarak tanımlanması gerekiyor. Bu işlemi *Control Panel* (Denetim Masası) &gt; *Manage User Accounts* (Kullanıcı Hesaplarını Yönet) penceresinden yapabiliriz.
4. Oluşturduğumuz kullanıcı, sunucuya uzak masaüstü bağlantısı yapacaksa (bu adım şart değil) ilgili yetkilerin verilmesi gerekiyor. Bunun için *Computer* (Bilgisayar) &gt; *Properties* (Özellikler) &gt; *Advanced System Settings* (Gelişmiş Sistem Ayarları) penceresinin *Remote* (Uzak) sekmesine geçerek uzak bağlantılara izin veriyor, *Select Users* (Kullanıcıları Seç) butonuna tıklayarak kullanıcımızı uzak bağlantı yapabilecek hale getiriyoruz.

**Adım 3:** Şimdi uygulamalarımızı geliştireceğimiz bir *Developer Site*si oluşturalım. Yine *Central Administration* sayfasından *Create Site Collections* linkine tıklayıp, buradan *Developer Site* oluşturabilir ve *Primary Site Collection Administrator* olarak biraz önce oluşturduğumuz kullanıcıyı seçebiliriz.
**Adım 4:** Şimdi uygulama geliştirmek için gereken *Service Application*'ları (servis uygulamaları) ve veritabanlarını oluşturmak için *SharePoint 2013 Management Shell*'i çalıştırıyor ve adım adım aşağıdaki kodları çalıştırıyoruz:

```powershell
$account = Get-SPManagedAccount "Administrator" 
$appPoolSubSvc = New-SPServiceApplicationPool -Name "Settings Service App Pool" -Account $account
$appSubSvc = New-SPSubscriptionSettingsServiceApplication –ApplicationPool $appPoolSubSvc –Name "Settings Service App" –DatabaseName "SettingsServiceDB"
$proxySubSvc = New-SPSubscriptionSettingsServiceApplicationProxy –ServiceApplication $appSubSvc
$appPoolAppSvc = New-SPServiceApplicationPool -Name AppServiceAppPool -Account $account
$appAppSvc = New-SPAppManagementServiceApplication -ApplicationPool $appPoolAppSvc -Name "Application Service App" -DatabaseName "AppServiceDB"
$proxyAppSvc = New-SPAppManagementServiceApplicationProxy -ServiceApplication $appAppSvc
```
**Not:** Bu örnekteki *Administrator* kullanıcısı benim tarafımdaki *Managed Account* oluyor. Siz hangisini seçeceğinizi bilmiyorsanız aynı pencerede ***Get-SPManagedAccount*** yazıp çalıştırarak *Managed Account*'ların listesini görebilirsiniz. Yukarıdaki kodların ne iş yaptığıyla ilgili uzun uzun açıklama yapabilecek durumda olmadığımdan sadece özünü sizlerle paylaştım. Detaylı bilgiye ihtiyacınız olursa [buradan](http://technet.microsoft.com/en-us/library/fp161236.aspx) konuyla ilgili açıklamalara ulaşabilirsiniz.
**Adım 5:** Uygulamalarımızı oluşturduğumuzda *SharePoint* bunlara belli bir yapıda URL'ler veriyor (*app-abcd1234.domain.com* gibi). Bu yüzden uygulamalarımız için kullanacağımız alan adını ve uygulama ön ekinin ne olacağını belirtmemiz gerekiyor. Bu işlem için *Central Administration* sayfasından *Apps* &gt;  *Configure App URLs* linkine tıklayıp, uygulamalarımız için bir alan adı ve ön ek seçiyoruz:
![sp2013-configure-app-urls](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/sp2013-configure-app-urls.png)
**Not:** Burada da değinmek istediğim bir nokta var. Bir sonraki adımda ilgili *DNS* ayarlarını yapacak ve keyfimize göre seçtiğimiz bu alan adını hosts dosyası ile de yönlendirecek olsak da, halihazırda kullanılmakta olan bir alan adı seçersek uygulamamızı çalıştırdığımızda dış siteye gitme problemiyle karşılaştım. Bu yüzden uygulamalarımız için seçtiğimiz alan adı, kullanılmayan bir alan adı olsun: *hasanapps.com* gibi.
**Adım 6:** Şimdi sıra geldi uygulamalarımız için kullanacağımız alan adı için *DNS* kayıtlarını oluşturmaya. Başlat menüsüne *DNS* yazıp *DNS Manager*'ı açıyor ve *Forward Lookup Zones*'u genişletip *SharePoint*'in kurulu olduğu domaine sağ tıklayarak (benim örneğimde hasan.local) yeni A kaydı oluşturuyoruz.
![dns-manager-new-host](ttps://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/dns-manager-new-host.png)
*IP Adresi* olarak ***127.0.0.1*** yazıp *Add Host* butonuna tıklayıp pencereyi kapatıyoruz. *Forward Lookup Zones*'a bu kez sağ tıklayarak *New Zone* diyor ve *Zone Name* olarak bir önceki adımda uygulamalarımız için seçtiğimiz alan adını yazıyoruz (bu yazı için *hasanapps.com* örneğinde olduğu gibi). Varsayılan seçeneklerle sihirbazı tamamlayıp alan adımıza ait kaydı oluşturduğumuzda, bu kayda sağ tıklayıp *New Alias (CNAME)* seçiyor ve aşağıdaki bilgileri giriyoruz:
**Alias name:** *
**Fully qualified domain name:** *Browse* butonuna tıklayıp, bu adımın başında *127.0.0.1* IP adresi ile oluşturduğumuz A kaydını seçiyoruz.
*OK* butonuna tıklayıp buradaki işimizi de bitirmiş oluyoruz. Son olarak *C:\Windows\System32\drivers\etc\* yolunda bulunan ***hosts*** dosyasını açıp, *127.0.0.1* IP adresini *SharePoint* adresimize yönlendiriyoruz (benim örneğim için ekran görüntülerindeki adres çubuğunda gördüğünüz üzere: *spf*)
```
127.0.0.1	spf
```
**Not:** Çeşitli kaynaklar konuyla alakalı açıklamalarında, bu *DNS* kayıtlarını oluşturduktan sonra rastgele oluşturduğunuz bir uygulama URL'sine ping attığınızda (*ping app-abc123.hasanapss.com*) cevap almanız gerektiğini yazmışlar. Birkaç bilgisayarda bu ortamı hazırladığımda yaptığım denemeler sonucu her zaman cevap alamadım. Ancak ping atamıyor olmak, uygulamaların çalışmasına engel olmadı. Uygulamanızı deploy ettikten sonra herhangi bir sorunla karşılaşmıyorsunuz, ping alacağım diye kendinizi paralamanıza gerek olmadığını belirtmek istiyorum :)
**Adım 7:** Bu aşamada uygulama geliştirmek için her şey hazır. Tek sorunumuz şu olacak: bir uygulama oluşturup deploy ettiğinizde, uygulamanız sizden sürekli oturum açmanızı isteyecek ama bir türlü oturum açılamayacak. Bu sorunu gidermek için de başlat menüsüne ***regedit*** yazıyor ve kayıt defterinde şu yolu izliyoruz:
```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa
```
Buraya *32 bit DWORD* ekleyip adını ***DisableLoopbackCheck***, değerini ***1*** olarak giriyoruz.
Ortamımız hazır. Artık uygulama geliştirmek için oluşturduğumuz kullanıcı ile sunucuda oturum açtıktan sonra *Visual Studio*'yu çalıştırıp (yönetici olarak) yeni bir *SharePoint-Hosted App* projesi oluşturabilir ve uygulamamızı deploy edebiliriz.
![sp2013-hello-user-app](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/sp2013-hello-user-app.png)

Ortamınız hayırlı olsun, hepinize kolay gelsin.
