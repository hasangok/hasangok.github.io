---
layout: post
title: Dev-C++ ile MPICH2 Kullanımı
date: 2014-01-14 22:49
author: hasangok
comments: true
Tags: [Bilgisayar, C, Dev-C++, MPI, MPICH2, Paralel Programlama, Programlar]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-584" style="margin: 2px 4px;" alt="dev-cpp-logo" src="http://www.hasangok.com.tr/wp-content/uploads/2014/01/dev-cpp-logo.jpg" width="160" height="160" />Çalışıyorum, çalışacağım derken (oldukça geç kalmış da olsam) <em>paralel programlama</em> konusunda ilk adımlarımı atmaktayım. Kullanmıış olduğum <em>C</em> kütüphanesi <strong><em>MPICH2</em></strong>'nin kurulumu ve kullanımı çeşitli kaynaklarda anlatılmış. Her kaynakta hemen hemen aynı şeylerin anlatıldığı açıklamaları takip ederek ben de ilk önce <em>Visual Studio 2013</em> ile bu kütüphaneyi kullandım ve örnek birkaç uygulama geliştirebildim. Ancak amaç konu mantığını anlamak ve olayı en basitte tutmak olduğundan, <em>Visual Studio</em>'ya <em>C++</em> özelliklerini eklemek yerine; modası geçmiş, terkedilmiş, bir çoğumuzun ilk programlama derslerinden hatırlayacağımız, vazgeçemediğimiz derleyicimiz <em>Dev-C++</em> ile bu kütüphanenin nasıl kullanılabileceğini araştırdım. Sonuçlar aşağıdaki gibi:</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;"><strong>Gereksinimler:</strong></p>

<ol style="text-align: justify;">
	<li><a href="http://www.microsoft.com/en-us/download/details.aspx?id=21" target="_blank">Buradan</a> indirebileceğiniz <em>Microsoft .NET Framework</em> yüklü olmalı.</li>
	<li><a href="http://www.microsoft.com/en-us/download/details.aspx?id=29" target="_blank">Buradan</a> indirebileceğiniz Microsoft <em>Visual C++</em> çalışma zamanı kütüphaneleri yüklü olmalı.</li>
	<li>Yönetici yetkilerine sahip bir kullanıcınız olmalı.</li>
</ol>
<p style="text-align: justify;"><strong>Kurulum:</strong></p>

<ol style="text-align: justify;">
	<li><em>MPICH2</em> kütüphanesini indirin ve yükleyin. (32 bit sürümünü <a href="http://www.mcs.anl.gov/research/projects/mpich2staging/goodell/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1-win-ia32.msi" target="_blank">buradan</a>, 64 bit sürümünü <a href="http://www.mcs.anl.gov/research/projects/mpich2staging/goodell/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1-win-x86-64.msi" target="_blank">şuradan</a> indirebilirsiniz, geçerli sürüm: <em>1.4.1p1</em>)</li>
	<li>Yönetici yetkili kullanıcı hesabınızı <strong><em>wmpiregister</em></strong> ile tanımlayın. (Başlat &gt; Tüm Programlar &gt; MPICH2 &gt; wmpiregister.exe ile)
<a href="http://www.hasangok.com.tr/wp-content/uploads/2014/01/mpiexec-register.png"><img class="size-full wp-image-585 aligncenter" alt="mpiexec-register" src="http://www.hasangok.com.tr/wp-content/uploads/2014/01/mpiexec-register.png" width="296" height="393" /></a></li>
</ol>
<p style="text-align: justify;"><strong>Dev-C++ ile Derleme:</strong></p>

<ol style="text-align: justify;">
	<li><em><span style="text-decoration: underline;">Dev-C++</span></em> derleyicisini yükleyin.</li>
	<li><em>MPI</em> Projesi şablonunu <a href="http://www.hasangok.com.tr/Tools/devcpp_mpi_tpl.zip" target="_blank">buradan</a> indirip "<em>C:\Dev-Cpp\Templates</em>" klasörü altına çıkarın.</li>
	<li>New &gt; Project yolunu izleyerek yeni bir <em>MPI</em> uygulaması oluşturun.
<img class="size-full wp-image-587 aligncenter" alt="new-mpi-project" src="http://www.hasangok.com.tr/wp-content/uploads/2014/01/new-mpi-project.png" width="514" height="299" /></li>
	<li>Şablon ile gelen kodları derleyin.</li>
</ol>
<p style="text-align: justify;"><strong>Paralel Uygulamamızı Çalıştırma:</strong></p>

<ol style="text-align: justify;">
	<li>Başlat &gt; Tüm Programlar &gt; MPICH2 &gt; wmpiexec.exe uygulamasını çalıştırın.</li>
	<li>Biraz önce derlemiş olduğunuz uygulamanızı seçin.</li>
	<li>Proses sayısını seçin ve <em>Execute</em> butonuna basın.
<img class="size-full wp-image-586 aligncenter" alt="mpiexec-wrapper" src="http://www.hasangok.com.tr/wp-content/uploads/2014/01/mpiexec-wrapper.png" width="520" height="383" /></li>
</ol>
<p style="text-align: justify;"><strong>Notlar:</strong></p>

<ol style="text-align: justify;">
	<li>Bu konuda derinlere dalmadan önce lütfen ders çalışın, ben yandım sizler yanmayın :)</li>
	<li>Yazdığınız kodları mutlaka <strong><em>wmpiexec</em></strong> ile çalıştırın, Windows konsolu uygulamanızı tek proseste çalıştıracaktır.</li>
	<li>Yine Windows konsoluna aldanıp, çalışıyor mu göreyim düşüncesi ve alışkanlığıyla <em><strong>getch()</strong></em> gibi bir fonksiyon kesinlikle kullanmayın, sonsuza kadar beklersiniz :)</li>
</ol>
<p style="text-align: justify;">Hepinize kolay gelsin.</p>
