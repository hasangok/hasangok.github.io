---
layout: post
title: SharePoint 2013 Liste İkonunu Değiştirmek
date: 2014-11-28 00:10
author: hasangok
comments: true
Tags: [Liste İşlemleri, PowerShell, SharePoint, Sharepoint 2013]
---
Site içeriğinde kare kare gördüğümüz liste ikonlarının değiştirilip değiştirilemeyeceği daha önceden hiç aklıma gelmemişti. Yöneticim "böyle bir şey var mı?" diye sorunca baktım, varmış. Listelerin **ImageUrl** özelliğine kullanmak istediğimiz ikon URL'ini vermemiz yeterli oluyor. Bunun için aşağıdaki PowerShell scriptini çalıştırabiliriz:

```powershell
$web = Get-SPWeb http://sp2013
$list = $web.Lists["TestList"]
$list.ImageUrl = "/SiteAssets/l_veripark.jpg"
$list.Update()
```
**Sonuç:**

![SharePoint 2013 Liste İkonunu](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/sharepoint-list-custom-icon.png "SharePoint 2013 Liste İkonunu")
