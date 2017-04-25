---
layout: post
title: Box, Yandex.Disk ve SkyDrive'ı Ağ Sürücüsü Olarak Eklemek
date: 2013-05-23 21:03
author: hasangok
comments: true
Tags: [Ağ Sürücüsüne Bağlan, Bilgisayar, box.com, Skydrive, Webdav, Yandex.Disk]
---
Masaüstünden dizüstü bilgisayara, HDD'den SSD'ye geçtiğimden beri bilgisayarımda alan sıkıntısı çekiyorum. 120 GB SSD, ne kadar dikkat edersem edeyim dolup taşıyor. Eskiden yukarıda bahsi geçen servislerin uygulamalarını bilgisayarıma yükler ve tüm dosyalarımı bilgisayarıma senkronize ederdim. Ancak SSD kullandığımdan beri bu pek mümkün olmuyor.
Lafı uzatmadan, tüm bu servislerdeki dosyalarıma erişebilmek için [Webdav](http://www.webdav.org) kullanarak hesaplarımı bilgisayarıma ağ sürücüsü olarak ekleyebiliyorum. Böylece bu hesaplarda sakladığım dosyaları bilgisayarıma senkronize etmemiş olsam bile istediğim zaman erişebiliyor, ya da ilgili yerlere dosyalarımı kopyalayabiliyorum. Dropbox ve Google Drive için de keşke aynısını yapabiliyor olsaydık, ancak Dropbox böyle bir çalışma yapmayacaklarını [web sayfasında](https://www.dropbox.com/help/62/en) belirtmiş, Google Drive ise bazı üçüncü parti araçlara ihtiyaç duyduğu için onu şimdilik pas geçiyorum.

**Yandex.Disk'i Ağ sürücüsü olarak eklemek için:**
1. *Bilgisayarım*ı açıp "*Ağ Sürücüsüne Bağlan*" tıklıyoruz.
2. *Klasör* alanına resimde görüldüğü şekilde "**https://webdav.yandex.com.tr/**" yazıyoruz ve "*Son*" a tıklıyoruz.
![yandex-disk-1](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/yandex-disk-1.png)
3. Gelen ekranda Yandex hesap bilgilerimizi girip "*Tamam*" butonuna tıklıyoruz.
![yandex-disk-2](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/yandex-disk-2.png)
4. *Yandex.Disk*'imiz hazır.
![yandex-disk-3](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/yandex-disk-3.png)

**SkyDrive'ı Ağ sürücüsü olarak eklemek için:**
1. https://skydrive.live.com adresine girip Microsoft hesabımızla oturum açıyoruz.
2. Sol alandaki *Dosyalar* linkine tıklayıp, adres çubuğuna eklenen ***"#cid=XXX"*** bölümündeki XXX kısmını kopyalıyoruz.
![skydrive-1](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/skydrive-1.png)
3. Bilgisayarımızdan "Ağ Sürücüsüne Bağlan" deyip, Klasör alanına "**https://d.docs.live.net/XXX**" yazıyoruz.
![skydrive-2](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/skydrive-2.png)
4. Microsoft hesabımızın bilgilerini girip *Tamam*'a tıklıyoruz.
![skydrive-3](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/skydrive-3.png)
5. *SkyDrive* kullanıma hazır.
![skydrive-4](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/skydrive-4.png)

**Box.com Hesabımızı Ağ sürücüsü olarak eklemek için:**
1. Bilgisayarımızı açıp "Ağ Sürücüsüne bağlan" diyoruz.
2. Klasör yolu olarak "**https://www.box.com/dav/**" yazıyoruz.
3. Box kullanıcı bilgilerimizi girip *Tamam*'a tıklıyoruz.
4. *Box* hesabımız kullanıma hazır.
![Box-1](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/05/Box-1.png)
