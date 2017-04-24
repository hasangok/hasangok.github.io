---
layout: post
title: PageNotFoundError.aspx Sayfasını Değiştirmek
date: 2015-06-09 13:11
author: hasangok
comments: true
Tags: [404, Genel, PageNotFoundError.aspx]
---
Kullanıcı gitmeye çalıştığı sayfaya ulaşamadığında, bu sıkıcı sayfayı göstermek yerine güzel tasarlanmış bir 404 sayfası göstermek isteriz. Bunun için aşağıdaki iki yoldan birini tercih edebiliriz:
<ol>
	<li><strong>PowerShell
</strong>Sharepoint 2013 Management Shell ekranında aşağıdaki satırları çalıştırmak.
<pre class="lang:ps decode:true  ">$spsite = Get-SPSite "http://sharepoint"
$spsite.FileNotFoundUrl = "/Pages/404.aspx"</pre>
</li>
	<li><strong>SharePoint Designer</strong>
Siteye bağlandığımızda sağ üstteki "<em>Site Options</em>" butonuna basıp "<em>vti_filenotfoundpage</em>" adlı kaydın değerini değiştirmek.
<img class="alignnone size-full wp-image-815" src="http://www.hasangok.com.tr/wp-content/uploads/2015/06/vti_filenotfoundpage.png" alt="vti_filenotfoundpage" width="428" height="373" /></li>
</ol>
İyi çalışmalar...
