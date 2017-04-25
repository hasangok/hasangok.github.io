---
layout: post
title: Client Object Model - Avantaj ve Dezavantajlar
date: 2013-08-21 15:43
author: hasangok
comments: true
Tags: [Client Object Model, Sharepoint, SharePoint]
---
Üzerinde çalıştığım son birkaç projedir *Client Object Model* kullanıyorum. Bugün ofiste böyle bir tartışma da çıkınca blogumda yer vermek istedim. İşte *Client Object Model*'in avantaj ve dezavantajları.
**Avantajlar:**

1. *JavaScript* kullanılarak kullanıcı tarafındaki web tarayıcısından *SharePoint* verilerine ulaşabiliyoruz.
2. *jQuery* yardımıyla zengin kullanıcı arayüzü olan web partlar geliştirebiliriz.
3. Visual Studio'ya gerek duymaksızın, sadece web tarayıcısı üzerinden, *İçerik Düzenleyicisi* web partı kullanarak istediğimiz web partları geliştirme şansına sahip oluruz.
4. Sitenizi şablon olarak kaydedip başka bir yere aktardığınızda, *Client Object Model* ile geliştirdiğiniz her şey de aktardığınız tarafta hazır bulunur.
5. *Client Object Model* kullanarak geliştirdiğiniz web partların çalışır hale gelmesi için deploy ya da iisreset gerekmez.
6. Geliştirme yapmak istediğiniz bilgisayarda *SharePoint*'in yüklü bulunması gerekmez.

**Dejavantajlar:**

1. Sunucu tarafında ihtiyaç duyduğumuz zaman yazdığımız *RunWithElevatedPrivilege* (burada bahsetmiştim) tarzı bir metod kullanma şansımız yok. Dolayısıyla sadece iznimiz kadar bilgiye ulaşabiliyoruz.
2. *Client Object Model*'de *SharePoint* verilerine ulaşmak için kullanabileceğimiz oldukça sınırlı sayıda sınıf var. Örneğin *User Profile* bilgilerine erişmemiz mümkün değil (*jQuery* ile *SharePoint* web servislerini kullanarak bu işlemi yapabiliyoruz).
3. Üzerinde çalıştığımız site collection'dan başka bir site collection üzerindeki veriye ulaşamıyoruz.
4. Ulaşmak istediğimiz veriler biraz gecikmeli gelebiliyor. Bu yüzden anlık sorgulama yapmamız gereken durumlarda sorunlar yaşanabiliyor.
