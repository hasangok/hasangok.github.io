---
layout: post
title: İlk Bakışta Windows 8.1
date: 2013-10-20 23:59
author: hasangok
comments: true
Tags: [Bilgisayar, Programlar, Windows 8, Windows 8.1]
---
Çok merak ediyormuşsunuz gibi dün [buradan](http://www.hasangok.com.tr/403/windows-8-1-guncellemesi.html) duyurmuştum Windows 8.1'e güncellediğimi. İlk bakışta gözüme çarpanları ve izlenimlerimi sizlere aktarmak için tekrar yazmak istedim.

1. Güncellemeyi *Windows 8 Mağazası* üzerinden yapmak zorundasınız, herhangi bir *ISO* dosyası bulunmuyor.
2. İşlem oldukça uzun sürüyor. İndirme işleminizi duraklatıp bilgisayarınızı kapatabilirsiniz. Bilgisayarınızı yeniden açıp tekrar indir dediğinizde, indirme işlemi kaldığı yerden devam ediyor.
3. *Windows 8*'de yerel hesap kullanıyordum, 8.1 güncellemesinden sonra *Microsoft hesabı* ile oturum açmanız isteniyor. Yerel hesap ile kesinlikle bilgisayarınızı açamıyorsunuz. Daha sonra bir yerel hesap oluşturup Microsoft hesabını kaldırmanız mümkün. Ancak böyle bir şey yapmanın gerekliliği tartışılır.
4. Başlangıç ekranındaki kutucukların renklendirmesi, ilgili uygulamanın ikonunun rengine göre belirleniyor. Bu da rengarenk bir başlangıç ekranı demek oluyor. Renk değişimini çok hoş buldum, eskisinden çok daha güzel. Buyrun görelim:
![windows-8.1-desktop](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/10/windows-8.1-desktop.png)
5. *Windows 8*'de olmayan *başlat tuşu* geri gelmiş, başlangıç ekranını açıyor. Pratikte hiçbir değişiklik yok anlayacağınız. Ancak eski bir dostu görmek de hoş.

Birden fazla monitör kullanıyorsanız, *Windows 8.1* farklı monitörler için farklı ***dpi*** değerleri seçiyor, bazı programlarda ölçekleme problemleri yaşadım. Düzeltmek için şu yolu izleyebilirsiniz:
1. *Masaüstü*ne sağ tıklayıp **Kişiselleştir**'i seçin.
2. Sol alt kısımda bulunan "*Ayrıca bkz.*" bölümünden **Görüntü**'ye tıklayın.
3. "*Tüm görüntülerim için bir ölçekleme düzeyi seçmeme izin ver*" kutucuğunu işaretleyin.
4. Bilgisayarınızı yeniden başlatın.
5. Görüntülerin ölçeklenmesiyle ilgili bir probleminiz kalmayacaktır.

*Microsoft hesabı* ile oturum açtığınızdan, bilgisayarınızı her açtığınızda bu hesabınızın parolasını girmeniz isteniyor. Bunu şöyle aşabiliyoruz:
1. Başlangıç ekranına "**netplwiz**" yazıp çalıştırın.
2. "*Kullanıcı bu bilgisayarı kullanmak için bir ad ve parola girmelidir*" kutucuğu önündeki işareti kaldırın.
3. **Uygula** veya **Tamam** dediğimizde gelen parola isteyen pencereye **Microsoft hesabımızın parolasını girmeliyiz**! Boş bırakıp kaydedersek oturum açarken hatalı parola diyecektir.
4. Ne kadar güvenilir olduğu tartışılır ancak o veya bu şekilde bir çözüm olarak kullanılabilir. Artık otomatik olarak oturum açabilirsiniz.

**Bilgisayar**ımızın adı "*Bu Bilgisayar*" olarak değişmiş. Artık sadece diskleri değil, *Belgeler*, *Müzikler* vb. gibi kütüphanelerimizin klasörlerini de gösteriyor. Bunları görmek istemiyorsanız şu adımları izleyebilirsiniz:

1. Başlangıç ekranına "**regedit**" yazıp *Kayıt Düzenleyicisi*ni açın.
2. **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Current Version\explorer\MyComputer\NameSpace** yolunu izleyin, ve aşağıdaki anahtarları silin.
```
{1CF1260C-4DD0-4ebb-811F-33C572699FDE} : *Müzikler* Klasörü
{374DE290-123F-4565-9164-39C4925E467B} : *İndirilenler* Klasörü
{3ADD1653-EB32-4cb0-BBD7-DFA0ABB5ACCA} : *Resimler* Klasörü
{A0953C92-50DC-43bf-BE83-3742FED03C9C} : *Videolar* Klasörü
{A8CDFF1C-4878-43be-B5FD-F8091C1C60D0} : *Bekgeler* Klasörü
{B4BFCC3A-DB2C-424C-B029-7FE99A87C641} : *Masaüstü*.
```

Başlangıç ekranı yerine direk masaüstüne düşmek istiyorsanız *Görev Çubuğu*nda sağ tıklayıp *Özellikler*'i seçtikten sonra, *Gezinti* sekmesinden "*Oturum açtığımda veya bir ekrandaki tüm uygulamaları kapattığımda Başlangıç yerine masaüstüne git*" kutucuğunu işaretleyebilirsiniz. Başlangıç ekranına alışmanız ise tavsiyemdir, doğru organize ettiğinizde daha kullanışlı olduğunu düşünüyorum.

Yukarıdaki problemler ilk an canımı sıksa da kolayca düzeltilebilir olduklarından olumsuz herhangi bir izlenimim yok. Zaten Windows 8'e iyice alışmışken yeniliklerinden de uzak kalmamak gerekir diye düşünüyor ve size de güncel kalmanızı tavsiye ediyorum.
Kalın sağlıcakla...
