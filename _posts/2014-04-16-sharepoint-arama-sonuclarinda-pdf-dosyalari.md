---
layout: post
title: SharePoint Arama Sonuçlarında PDF Dosyaları
date: 2014-04-16 14:50
author: hasangok
comments: true
Tags: [Full Crawl, PDF, Search Service, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><img class="alignleft  wp-image-672" style="margin: 1px;" alt="search-pdf" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/04/search-pdf.jpg" width="93" height="117" />Doküman kütüphanemizde yüklü bulunan <em>PDF</em> dosyalarına <em>SharePoint</em> aramaları vasıtasıyla ulaşırken şöyle bir sorunla karşılaştık: Arama sonuçlarındaki linkler dosyalarımızı değil, ilgili dosyanın <em>DispForm.aspx</em> linklerine işaret ediyordu. Bu durum Word, Excel gibi doslayar için söz konusu olmadığından <em>DispForm.aspx</em> sayfası yerine, direk <em>PDF</em> dosyalarımızı işaret etmemiz bir zorunluluk haline geldi.</p>
<p style="text-align: justify;"><em>Adobe</em> tarafından sunulan ve PDF dosyalarının Windows hizmetleri tarafından indekslenebilmesini sağlayan <em>iFilter</em> paketiyle ilgili birkaç deneme yapsam da bu yöntemde başarı olamadım. Sonrasında yaptığım araştırmalar doğrultusunda aşağıdaki adımları izleyerek arama sonuçlarındaki <em>PDF</em> dosyalarını direk linkleyebilmeyi başardım.</p>
<p style="text-align: justify;"><!--more--></p>
<p style="text-align: justify;">İlk olarak yapmamız gereken <em>Central Administration</em> &gt; <em>Manage Service Applications</em> &gt; <em>Search Service Application</em> yolunu izleyip <em>Crawling</em> başlığı altından <em><strong>File Types</strong></em> linkine tıklayarak <em>PDF</em>'yi bir uzantı olarak eklemek.</p>
<p style="text-align: justify;"><img class="alignleft size-full wp-image-673" alt="new-file-type" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/04/new-file-type.png" width="745" height="164" /></p>
<p style="text-align: justify;">Bu işlemden hemen sonra <em>Administrative Tools</em> (<em>Yönetimsel Araçlar</em>) altında bulunan <em><strong>Services</strong> </em>uygulamasını çalıştırıyor ve <em>SharePoint Server Search 14</em> servisini yeniden başlatıyoruz (<em>Restart</em>).</p>
<p style="text-align: justify;">Daha sonra <em>Central Administration</em> &gt; <em>Manage Service Applications</em> &gt; <em>Search Service Application</em> yolunu izleyip <em>Crawling</em> başlığı altındaki <strong><em>Index Reset</em></strong> linkine tıklıyor ve tüm indekslenmiş içeriğimizi sıfırlıyoruz. Bunun ardından <strong><em>Content Sources</em></strong> linkine tıklatıp "<em>Start Full Crawl</em>" diyor ve içeriğimizin büyüklüğüne göre uzunca bir süre bekliyoruz.</p>
<p style="text-align: justify;"><em>Full Crawl</em> tamamlandıktan sonra arama sonuçlarındaki <em>PDF</em> içerikleriniz de direk olarak ilgili dosyaya işaret ediyor olacak.</p>
