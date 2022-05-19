---
title: Central Administration Sitesine Ulaşamama Problemi
date: 2014-07-31 17:40
---

Bugün yine canımız cananımız *SharePoint*'in bir sorunuyla karşılaşıp çözümünü tecrübe ettiğim için not etmek istedim.

2 adet *SharePoint* sunucusu bulunan farmımızdan, bu sunuculardan bir tanesini çıkarmamız gerekti. Her iki sunucu üzerinde de *Central Administration* (kısaca *CA*) sitesi bulunuyordu, ancak *CA* sitesine ulaştığımız adres (url) farmdan çıkaracağımız servera işaret ediyordu. Farmda kalacak sunucu üzerinde de *Central Administration* bulunduğundan ve çıkarma işlemini "**SharePoint 2010 Products Configuration Wizard**" ile yapacağımızdan, iç taraftaki güncellemeleri *SharePoint* yapacaktır diye düşünmüştüm. Tabi ki yanılmışım 🙂

<!--more-->
Sunucuyu farmdan çıkardıktan sonra artık *CA* sitesine ulaşılamıyordu. Sorunu çözmek için aşağıdaki yolu izleyebiliriz:

**1.** Farmda kalan sunucuda *SharePoint 2010 Products Configuration Wizard*'ı çalıştırıp ilerlerken **Host Central Administration Web Application** başlığına geldiğimizde aşağıdaki ekran görüntüsündeki gibi "*Use this machine to host the web site*" seçiyoruz.

![Use-this-machine-to-host-the-web-site](/uploads/2014/07/Use-this-machine-to-host-the-web-site.jpg "Use-this-machine-to-host-the-web-site")

**2.** *SharePoint 2010 Products Configuration Wizard* başarıyla tamamlandığında *CA* sitesinin url'ini başarıyla güncellediğini görüyoruz. Ancak *Finish*'e tıkladığımızda halen eski url'i açmaya çalışıyor. Aynı şekilde başlat menüsündeki *Central Administration* linki de bizi eski sunucuya göndermeye çalışıyor. Daha enteresan olanı tarayıcımızda *http://yenisunucu:yeniport* şeklinde ulaşırsak sayfa görüntülenemezken, *http://yenisunucu:yeniport/default.aspx* şeklinde yazdığımızda sayfaya ulaşabiliyor.

**3.** Bu aşamada *default.aspx* ile birlikte *CA* sitemizi görüntüleyip *System Settings* &gt; *Configure Alternate Access Mappings* bölümüne geçiyoruz. *CA* için oluşturulmuş ve eski sunucuyu işaret eden kayıtları düzenleyip, eski url'leri yenileriyle değiştirip kaydediyoruz.

**4.** Bu aşamada herşeyin tamamlanmış olmasını bekliyoruz. Evet, kontrol ediyoruz... Tabi ki halen eski sunucuya yönlendiriliyoruz 🙂 Şimdi de **regedit.exe** programını çalıştırıp şu yolu izliyoruz:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Shared Tools\Web Server Extensions\14.0\WSS\
```
**5.** Buradaki **CentralAdministrationURL** değerini *http://yenisunucu:yeniport/* şeklinde değiştirip kaydediyoruz.

Artık *CA* sitesi yeni adresinden ve tüm linkler aracılığıyla erişilebilir durumda.

İyi çalışmalar.
