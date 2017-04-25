---
layout: post
title: SharePoint Arama Sonuçlarında PDF Dosyaları
date: 2014-04-16 14:50
author: hasangok
comments: true
Tags: [Full Crawl, PDF, Search Service, Sharepoint, SharePoint]
---
![search-pdf](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/04/search-pdf.jpg "search-pdf")

Doküman kütüphanemizde yüklü bulunan *PDF* dosyalarına *SharePoint* aramaları vasıtasıyla ulaşırken şöyle bir sorunla karşılaştık: Arama sonuçlarındaki linkler dosyalarımızı değil, ilgili dosyanın *DispForm.aspx* linklerine işaret ediyordu. Bu durum Word, Excel gibi doslayar için söz konusu olmadığından *DispForm.aspx* sayfası yerine, direk *PDF* dosyalarımızı işaret etmemiz bir zorunluluk haline geldi.
*Adobe* tarafından sunulan ve PDF dosyalarının Windows hizmetleri tarafından indekslenebilmesini sağlayan *iFilter* paketiyle ilgili birkaç deneme yapsam da bu yöntemde başarı olamadım. Sonrasında yaptığım araştırmalar doğrultusunda aşağıdaki adımları izleyerek arama sonuçlarındaki *PDF* dosyalarını direk linkleyebilmeyi başardım.

İlk olarak yapmamız gereken *Central Administration* &gt; *Manage Service Applications* &gt; *Search Service Application* yolunu izleyip *Crawling* başlığı altından ***File Types*** linkine tıklayarak *PDF*'yi bir uzantı olarak eklemek.
![new-file-type](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/04/new-file-type.png "new-file-type")

Bu işlemden hemen sonra *Administrative Tools* (*Yönetimsel Araçlar*) altında bulunan ***Services** *uygulamasını çalıştırıyor ve *SharePoint Server Search 14* servisini yeniden başlatıyoruz (*Restart*).
Daha sonra *Central Administration* &gt; *Manage Service Applications* &gt; *Search Service Application* yolunu izleyip *Crawling* başlığı altındaki ***Index Reset*** linkine tıklıyor ve tüm indekslenmiş içeriğimizi sıfırlıyoruz. Bunun ardından ***Content Sources*** linkine tıklatıp "*Start Full Crawl*" diyor ve içeriğimizin büyüklüğüne göre uzunca bir süre bekliyoruz.
*Full Crawl* tamamlandıktan sonra arama sonuçlarındaki *PDF* içerikleriniz de direk olarak ilgili dosyaya işaret ediyor olacak.
