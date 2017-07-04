---
layout: post
title: An object in the SharePoint administrative framework, "SPSolutionLanguagePack Name=0", depends on other objects which do not exist.
date: 2017-07-04 10:50
author: hasangok
comments: true
Tags: [SharePoint]
---

Sunucuda mevcut bir paketi retract/uninstall yaptıktan hemen sonra tekrar eklemeye çalıştığımızda aşağıdaki hatayı almak muhtemel. Sebebi, paketi sildikten sonra arka planda çalışmaya devam eden temizlik işleri bitmeden aynı paketi tekrar eklemeye çalışıyor olmamız.
```
Add-SPSolution : An object in the SharePoint administrative framework, "SPSolutionLanguagePack Name=0",  
depends on other objects which do not exist. Ensure that all of the objects dependencies are created  
and retry this operation.
```
Bir süre bekleyip tekrar denemek bir çözüm olabileceği gibi, beklediğimiz halde halen sorun devam ediyorsa aşağıdaki adımları takip edebiliriz:

1. **SharePoint Timer Service**'i durduralım.
2. *C:\Documents and Settings\All Users\Application Data\Microsoft\SharePoint\Config* klasörü altındaki **Cache.ini** dosyalarını yedekleyelim.
3. GUID adlı klasörlerdeki tüm **xml** dosyalarını silelim.
4. Cache.ini dosyalarının içerisindekileri temizleyip **1** yazarak kaydedelim.
5. **SharePoint Timer Service**'i tekrar başlatalım.

Bu adımlardan sonra paketimizi sorunsuz ekleyebileceğiz.
