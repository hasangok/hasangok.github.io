---
title: SharePoint 2013 - The tool was unable to install Application Server Role, Web Server (IIS) Role
date: 2014-08-22 09:52
---

Bugün *Wndows Server 2012* üzerinde *SharePoint 2013* kurulumu yapmaya hazırlanırken *SharePoint 2013 Products Preparation Tool* başlıktaki hatayı verdi. Oldukça popüler bir hata olduğundan olsa gerek çeşit çeşit çözüm önerileri sunulmuş ve her bir öneri birilerinin hatasını gidermiş. Benim için çözüm olan yöntem ise şu şekildeydi:

<!--more-->
1. Başlat ekranına *MMC* yazıp çalıştırıyoruz.
2. *File* menüsünden *Add/Remove Snap-in* seçiyoruz.
3. *Group Policy Object Editor* seçip ekliyoruz.
4. *Computer Management* &gt; *Administrative Templates* &gt; *System* yolunu izliyoruz.
5. "*Specify Settings for optional component installation and component repair*" seçiyoruz.
6. *Enable* seçip "*Contract Windows Update directly to download repair content instead of Windows Server Update Services (WSUS)*" önündeki checkbox'ı işaretliyoruz.

Bu adımları izledikten sonra Preparation Tool IIS'i kurup devam edebildi.

İyi çalışmalar.
