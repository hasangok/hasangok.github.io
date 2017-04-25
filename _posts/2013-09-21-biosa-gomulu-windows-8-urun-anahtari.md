---
layout: post
title: BIOS'a Gömülü Windows 8 Ürün Anahtarı
date: 2013-09-21 20:17
author: hasangok
comments: true
Tags: [Bilgisayar, BIOS'taki Ürün Anahtarı, Programlar, Windows 8]
---
![Windows-8-logo](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/08/Windows-8-Logo-small.png)
Bilgisayarımın bozulduğunu daha önce yazmıştım. *ASUS* ürün değişimi kararı verip, Teknosa yeni bilgisayarımı getirdiği zaman bu kez ilk işim yüklü gelen ürün anahtarını alıp bir kenara not etmek oldu. Bilgisayarda yüklü olan *Windows*'un ürün anahtarını öğrenmek için ***Windows 8 Product Key Viewer*** adlı [bu aracı](http://www.hasangok.com.tr/Tools/wpkey_v1.4.7d.zip) kullanabilirsiniz. Yanlız bu araç BIOS'taki ürün anahtarını değil, yükleme sırasında kullanılan ürün anahtarını gösteriyor. Yeni aldığınız, *Windows 8* yüklü olarak gelen bilgisayarlarda her ikisi de aynı olmalı.
*BIOS*'a gömülü ürün anahtarını öğrenmek için ise ***RWEverything*** isimli uygulamaya ihtiyacımız var. Bu uygulamanın 64bit portable sürümünü [buraya(http://www.hasangok.com.tr/Tools/RwPortableX64V1.6.4.zip) tıklayarak edinebilirsiniz. Ürün anahtarımızı görebilmek için öncelikle uygulamayı yönetici izinleriyle çalıştırıyoruz:
![rweverything-main](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/rweverything-main.png)
Burada kırmızı ile işaretlediğim **ACPI** butonuna tıklıyoruz, açılan pencereden ise **MSDM** sekmesine geçiyoruz.
![rweverything-acpi-msdm](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/09/rweverything-acpi-msdm.png)
Kırmızı içine alıp siyahla üzerini çizdiğim alanlarda *BIOS*'ta kayıtlı *Windows 8 lisans anahtarı*nız yer alıyor.
Sırf merakımdan, kontrollü deneyini de yapmış olmak için, bilgisayarıma farklı bir *Windows 8* sürümünü, farklı bir ürün anahtarıyla kurup her iki araç ile de tekrar kontrol ettim. Bahsi geçen ilk araç yükleme sırasında kullandığım ürün anahtarını gösterirken, *RWEverything*'de yine *BIOS*'taki ürün anahtarımı gördüm. Gerçekten *BIOS*'taki ürün anahtarıma erişebildiğimi kendi kendime kanıtladığım için tekrar orjinal *Windows*'uma geri dönüş yaptım. Yaşasın boş zamanlar! :)
