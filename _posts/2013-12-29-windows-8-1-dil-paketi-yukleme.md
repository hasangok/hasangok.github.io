---
layout: post
title: Windows 8.1 Dil Paketi Yükleme
date: 2013-12-29 22:36
author: hasangok
comments: true
Tags: [Bilgisayar, Dil Paketi, lp.cab, Windows 8.1]
---
*Windows 8.1* için dil paketlerini içeren ISO dosyasını indirdiğimizde, bu paketlerin kurulumu ile alakalı herhangi bir bilgi bulamıyoruz. İçerisinde yükleme için herhangi bir uygulama da yok. Sadece her dil için oluşturulmuş bir klasör ve her klasör altında **lp.cab** adında dosyalar bulunuyor. *Denetim Masası* altındaki dil seçenekleri de *Windows* arayüzünü Türkçeleştirmek için indirdiğimiz bu **lp.cab** dosyalarını yükleyebileceğimiz bir araç sunmuyor. İndirdiğimiz bu dosyaları kullanarak dil paketlerini yüklemek için iki yol var:

1. Başlat ekranına ***lpksetup*** yazarak karşımıza gelen sihirbaz ile bu dosyaları sistemimize yükleyebiliyoruz.
![lpksetup](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/lpksetup.png)
2. Yönetici olarak çalıştırdığımız bir *Komut İstemi* (cmd.exe) penceresinde aşağıdaki satırı çalıştırabiliriz:
```
dism /online /add-package /packagepath:D:\tr-tr\lp.cab
```

Her iki seçenekten sonra da *Denetim Masası*'nda dil seçeneklerine giderek yüklediğimiz paketi aktifleştirmemiz gerekebilir.
Kolay gelsin...
