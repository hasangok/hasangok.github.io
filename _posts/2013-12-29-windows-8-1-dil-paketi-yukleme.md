---
layout: post
title: Windows 8.1 Dil Paketi Yükleme
date: 2013-12-29 22:36
author: hasangok
comments: true
Tags: [Bilgisayar, Dil Paketi, lp.cab, Windows 8.1]
---
<p style="text-align: justify;"><em>Windows 8.1</em> için dil paketlerini içeren ISO dosyasını indirdiğimizde, bu paketlerin kurulumu ile alakalı herhangi bir bilgi bulamıyoruz. İçerisinde yükleme için herhangi bir uygulama da yok. Sadece her dil için oluşturulmuş bir klasör ve her klasör altında <strong>lp.cab</strong> adında dosyalar bulunuyor. <em>Denetim Masası</em> altındaki dil seçenekleri de <em>Windows</em> arayüzünü Türkçeleştirmek için indirdiğimiz bu <strong>lp.cab</strong> dosyalarını yükleyebileceğimiz bir araç sunmuyor. İndirdiğimiz bu dosyaları kullanarak dil paketlerini yüklemek için iki yol var:</p>
<p style="text-align: justify;"><!--more--></p>

<ol style="text-align: justify;">
	<li>Başlat ekranına <em><strong>lpksetup</strong></em> yazarak karşımıza gelen sihirbaz ile bu dosyaları sistemimize yükleyebiliyoruz.
<img class="aligncenter size-full wp-image-561" alt="lpksetup" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2013/12/lpksetup.png" width="623" height="439" /></li>
	<li>Yönetici olarak çalıştırdığımız bir <em>Komut İstemi</em> (cmd.exe) penceresinde aşağıdaki satırı çalıştırabiliriz:
<pre class="lang:default decode:true">dism /online /add-package /packagepath:D:\tr-tr\lp.cab</pre>
</li>
</ol>
<p style="text-align: justify;">Her iki seçenekten sonra da <em>Denetim Masası</em>'nda dil seçeneklerine giderek yüklediğimiz paketi aktifleştirmemiz gerekebilir.</p>
<p style="text-align: justify;">Kolay gelsin...</p>
