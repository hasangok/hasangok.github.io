---
layout: post
title: PageNotFoundError.aspx Sayfasını Değiştirmek
date: 2015-06-09 13:11
author: hasangok
comments: true
Tags: [404, Genel, PageNotFoundError.aspx]
---
Kullanıcı gitmeye çalıştığı sayfaya ulaşamadığında, bu sıkıcı sayfayı göstermek yerine güzel tasarlanmış bir 404 sayfası göstermek isteriz. Bunun için aşağıdaki iki yoldan birini tercih edebiliriz:

1. **PowerShell**:
Sharepoint 2013 Management Shell ekranında aşağıdaki satırları çalıştırmak.
```powershell
$spsite = Get-SPSite "http://sharepoint"
$spsite.FileNotFoundUrl = "/Pages/404.aspx"
```
2. **SharePoint Designer**:
Siteye bağlandığımızda sağ üstteki "*Site Options*" butonuna basıp "*vti_filenotfoundpage*" adlı kaydın değerini değiştirmek.

![vti_filenotfoundpage](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2015/06/vti_filenotfoundpage.png "vti_filenotfoundpage")

İyi çalışmalar...
