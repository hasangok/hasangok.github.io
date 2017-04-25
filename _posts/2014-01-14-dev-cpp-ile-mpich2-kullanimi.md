---
layout: post
title: Dev-C++ ile MPICH2 Kullanımı
date: 2014-01-14 22:49
author: hasangok
comments: true
Tags: [Bilgisayar, C, Dev-C++, MPI, MPICH2, Paralel Programlama, Programlar]
---
![dev-cpp-logo](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/01/dev-cpp-logo.jpg "dev-cpp-logo")

Çalışıyorum, çalışacağım derken (oldukça geç kalmış da olsam) *paralel programlama* konusunda ilk adımlarımı atmaktayım. Kullanmıış olduğum *C* kütüphanesi ***MPICH2***'nin kurulumu ve kullanımı çeşitli kaynaklarda anlatılmış. Her kaynakta hemen hemen aynı şeylerin anlatıldığı açıklamaları takip ederek ben de ilk önce *Visual Studio 2013* ile bu kütüphaneyi kullandım ve örnek birkaç uygulama geliştirebildim. Ancak amaç konu mantığını anlamak ve olayı en basitte tutmak olduğundan, *Visual Studio*'ya *C++* özelliklerini eklemek yerine; modası geçmiş, terkedilmiş, bir çoğumuzun ilk programlama derslerinden hatırlayacağımız, vazgeçemediğimiz derleyicimiz *Dev-C++* ile bu kütüphanenin nasıl kullanılabileceğini araştırdım. Sonuçlar aşağıdaki gibi:

**Gereksinimler:**
1. [Buradan](http://www.microsoft.com/en-us/download/details.aspx?id=21) indirebileceğiniz *Microsoft .NET Framework* yüklü olmalı.
2. [Buradan](http://www.microsoft.com/en-us/download/details.aspx?id=29) indirebileceğiniz Microsoft *Visual C++* çalışma zamanı kütüphaneleri yüklü olmalı.
3. Yönetici yetkilerine sahip bir kullanıcınız olmalı.

**Kurulum:**

1. *MPICH2* kütüphanesini indirin ve yükleyin. (32 bit sürümünü [buradan](http://www.mcs.anl.gov/research/projects/mpich2staging/goodell/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1-win-ia32.msi), 64 bit sürümünü [şuradan](http://www.mcs.anl.gov/research/projects/mpich2staging/goodell/downloads/tarballs/1.4.1p1/mpich2-1.4.1p1-win-x86-64.msi) indirebilirsiniz, geçerli sürüm: *1.4.1p1*)
2. Yönetici yetkili kullanıcı hesabınızı ***wmpiregister*** ile tanımlayın. (Başlat &gt; Tüm Programlar &gt; MPICH2 &gt; wmpiregister.exe ile)
![mpiexec-register](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/01/mpiexec-register.png "mpiexec-register")

**Dev-C++ ile Derleme:**

1. *Dev-C++* derleyicisini yükleyin.
2. *MPI* Projesi şablonunu [buradan](http://www.hasangok.com.tr/Tools/devcpp_mpi_tpl.zip) indirip "*C:\Dev-Cpp\Templates*" klasörü altına çıkarın.
3. New &gt; Project yolunu izleyerek yeni bir *MPI* uygulaması oluşturun.
![new-mpi-project](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/01/new-mpi-project.png "new-mpi-project")
4. Şablon ile gelen kodları derleyin.
</ol>
**Paralel Uygulamamızı Çalıştırma:**

1. Başlat &gt; Tüm Programlar &gt; MPICH2 &gt; wmpiexec.exe uygulamasını çalıştırın.
2. Biraz önce derlemiş olduğunuz uygulamanızı seçin.
3. Proses sayısını seçin ve *Execute* butonuna basın.
![mpiexec-wrapper](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/01/mpiexec-wrapper.png)

**Notlar:**

1. Bu konuda derinlere dalmadan önce lütfen ders çalışın, ben yandım sizler yanmayın :)
2. Yazdığınız kodları mutlaka ***wmpiexec*** ile çalıştırın, Windows konsolu uygulamanızı tek proseste çalıştıracaktır.
3.Yine Windows konsoluna aldanıp, çalışıyor mu göreyim düşüncesi ve alışkanlığıyla ***getch()*** gibi bir fonksiyon kesinlikle kullanmayın, sonsuza kadar beklersiniz :)

Hepinize kolay gelsin.
