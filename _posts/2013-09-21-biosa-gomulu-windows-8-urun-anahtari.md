---
layout: post
title: BIOS'a Gömülü Windows 8 Ürün Anahtarı
date: 2013-09-21 20:17
author: hasangok
comments: true
Tags: [Bilgisayar, BIOS'taki Ürün Anahtarı, Programlar, Windows 8]
---
<p style="text-align: justify;"><img class="alignleft size-thumbnail wp-image-156" alt="Windows-8-logo" src="http://www.hasangok.com.tr/wp-content/uploads/2013/08/Windows-8-Logo-small-150x150.png" width="150" height="150" />Bilgisayarımın bozulduğunu daha önce <a title="Yetkili Servis: Asus vs. Lenovo" href="http://www.hasangok.com.tr/325/yetkili-servis-asus-vs-lenovo.html" target="_blank">burada</a> yazmıştım. <em>ASUS</em> ürün değişimi kararı verip, Teknosa yeni bilgisayarımı getirdiği zaman bu kez ilk işim yüklü gelen ürün anahtarını alıp bir kenara not etmek oldu. Bilgisayarda yüklü olan <em>Windows</em>'un ürün anahtarını öğrenmek için <strong><em>Windows 8 Product Key Viewer</em></strong> adlı <a href="http://www.hasangok.com.tr/Tools/wpkey_v1.4.7d.zip" target="_blank">bu aracı</a> kullanabilirsiniz. Yanlız bu araç BIOS'taki ürün anahtarını değil, yükleme sırasında kullanılan ürün anahtarını gösteriyor. Yeni aldığınız, <em>Windows 8</em> yüklü olarak gelen bilgisayarlarda her ikisi de aynı olmalı.</p>
<p style="text-align: justify;"><em>BIOS</em>'a gömülü ürün anahtarını öğrenmek için ise <strong><em>RWEverything</em></strong> isimli uygulamaya ihtiyacımız var. Bu uygulamanın 64bit portable sürümünü <a href="http://www.hasangok.com.tr/Tools/RwPortableX64V1.6.4.zip" target="_blank">buraya</a> tıklayarak edinebilirsiniz. Ürün anahtarımızı görebilmek için öncelikle uygulamayı yönetici izinleriyle çalıştırıyoruz:</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-335" alt="rweverything-main" src="http://www.hasangok.com.tr/wp-content/uploads/2013/09/rweverything-main.png" width="976" height="547" /></p>
<p style="text-align: justify;">Burada kırmızı ile işaretlediğim <strong>ACPI</strong> butonuna tıklıyoruz, açılan pencereden ise <strong>MSDM</strong> sekmesine geçiyoruz.</p>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-336" alt="rweverything-acpi-msdm" src="http://www.hasangok.com.tr/wp-content/uploads/2013/09/rweverything-acpi-msdm.png" width="976" height="659" /></p>
<p style="text-align: justify;">Kırmızı içine alıp siyahla üzerini çizdiğim alanlarda <em>BIOS</em>'ta kayıtlı <em>Windows 8 lisans anahtarı</em>nız yer alıyor.</p>
<p style="text-align: justify;">Sırf merakımdan, kontrollü deneyini de yapmış olmak için, bilgisayarıma farklı bir <em>Windows 8</em> sürümünü, farklı bir ürün anahtarıyla kurup her iki araç ile de tekrar kontrol ettim. Bahsi geçen ilk araç yükleme sırasında kullandığım ürün anahtarını gösterirken, <em>RWEverything</em>'de yine <em>BIOS</em>'taki ürün anahtarımı gördüm. Gerçekten <em>BIOS</em>'taki ürün anahtarıma erişebildiğimi kendi kendime kanıtladığım için tekrar orjinal <em>Windows</em>'uma geri dönüş yaptım. Yaşasın boş zamanlar! :)</p>
