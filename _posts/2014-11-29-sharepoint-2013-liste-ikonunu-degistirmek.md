---
layout: post
title: SharePoint 2013 Liste İkonunu Değiştirmek
date: 2014-11-29 00:10
author: hasangok
comments: true
Tags: [Liste İşlemleri, PowerShell, SharePoint, Sharepoint 2013]
---
<p style="text-align: justify;">Site içeriğinde kare kare gördüğümüz liste ikonlarının değiştirilip değiştirilemeyeceği daha önceden hiç aklıma gelmemişti. Yöneticim "böyle bir şey var mı?" diye sorunca baktım, varmış. Listelerin <strong>ImageUrl</strong> özelliğine kullanmak istediğimiz ikon URL'ini vermemiz yeterli oluyor. Bunun için aşağıdaki PowerShell scriptini çalıştırabiliriz:</p>

<pre class="lang:default decode:true ">$web = Get-SPWeb http://sp2013
$list = $web.Lists["TestList"]
$list.ImageUrl = "/SiteAssets/l_veripark.jpg"
$list.Update()</pre>
<strong>Sonuç:</strong>

<img class="alignnone size-full wp-image-783" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/sharepoint-list-custom-icon.png" alt="sharepoint-list-custom-icon" width="949" height="504" />
