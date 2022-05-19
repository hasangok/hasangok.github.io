---
title: SharePoint Designer Önbelleğini Silmek
date: 2014-04-14 12:35
---

SharePoint Designer ile düzenlediğimiz dosyalar zaman zaman dengesiz davranışlar sergileyebiliyor. Check-in, check-out gibi işlemlerde dosyaları kaydetmeye çalışırken, ya da SharePoint sitemize bağlantı kurma sırasında çeşitli sorunlarla karşılaşabiliyoruz. Bu gibi sorunlarla karşılaştığımızda SharePoint Designer'ın önbelleğini temizlemek bazen çözüm olabiliyor. Önbelleği temizlemek için aşağıdaki klasörlerin içeriklerini silmek gerekiyor:

<!--more-->
```
%APPDATA%\Microsoft\Web Server Extensions\Cache
%USERPROFILE%\AppData\Local\Microsoft\WebsiteCache
```
