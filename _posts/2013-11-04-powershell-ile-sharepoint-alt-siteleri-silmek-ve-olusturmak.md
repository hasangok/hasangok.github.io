---
title: PowerShell ile SharePoint Alt Siteleri Silmek ve Oluşturmak
date: 2013-11-04 12:07
---

*Sharepoint 2013* arayüzünden alt site oluşturmaya çalıştığımda anlamsız bir şekilde işlem yarım kalıyor ve başlıksız alt siteler oluşuyor. Sorunu irdelemeye vaktim olmadığından *PowerShell* imdadıma yetişti ve iki satır kod ile bozuk siteleri silip yenilerini oluşturabildim. *SharePoint Management Shell*'i açıp aşağıdaki kodları kullanabiliriz.

<!--more-->
**Herhangi bir alt siteyi silmek için**:
```powershell
Remove-SPWeb http://sharepointURL/altsite
```
**Yeni bir alt site oluşturmak için:**
```powershell
New-SPWeb -url http://sharepointURL/altsite -name "Yeni Alt Site" -template STS#0
```
Burada *STS#0* alt sitemizin bir *Ekip Sitesi* (*Team Site*) olacağını belirtiyor. Tüm site şablonları için *Get-SPWebTemplate* komutu kullanılabilir.

Kolay gelsin...
