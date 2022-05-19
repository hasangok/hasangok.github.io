---
title: SharePoint 2013 Liste İkonunu Değiştirmek
date: 2014-11-28 00:10
---

Site içeriğinde kare kare gördüğümüz liste ikonlarının değiştirilip değiştirilemeyeceği daha önceden hiç aklıma gelmemişti. Yöneticim "böyle bir şey var mı?" diye sorunca baktım, varmış. Listelerin **ImageUrl** özelliğine kullanmak istediğimiz ikon URL'ini vermemiz yeterli oluyor. Bunun için aşağıdaki PowerShell scriptini çalıştırabiliriz:

<!--more-->
```powershell
$web = Get-SPWeb http://sp2013
$list = $web.Lists["TestList"]
$list.ImageUrl = "/SiteAssets/l_veripark.jpg"
$list.Update()
```
**Sonuç:**

![SharePoint 2013 Liste İkonunu](/uploads/2014/11/sharepoint-list-custom-icon.png "SharePoint 2013 Liste İkonunu")
