---
layout: post
title: PowerShell ile SharePoint Alt Siteleri Silmek ve Oluşturmak
date: 2013-11-04 12:07
author: hasangok
comments: true
Tags: [PowerShell, PowerShell, Sharepoint, SharePoint, Sharepoint 2013, SharePoint Management Shell]
---
<p style="text-align: justify;"><em>Sharepoint 2013</em> arayüzünden alt site oluşturmaya çalıştığımda anlamsız bir şekilde işlem yarım kalıyor ve başlıksız alt siteler oluşuyor. Sorunu irdelemeye vaktim olmadığından <em>PowerShell</em> imdadıma yetişti ve iki satır kod ile bozuk siteleri silip yenilerini oluşturabildim. <em>SharePoint Management Shell</em>'i açıp aşağıdaki kodları kullanabiliriz.</p>
<p style="text-align: justify;">Herhangi bir alt siteyi silmek için:</p>

<pre class="lang:default decode:true">Remove-SPWeb http://sharepointURL/altsite</pre>
<p style="text-align: justify;"><span style="text-align: justify;">Yeni bir alt site oluşturmak için:</span></p>

<pre class="lang:default decode:true">New-SPWeb –url http://sharepointURL/altsite -name "Yeni Alt Site" -template STS#0</pre>
<p style="text-align: justify;">Burada <em>STS#0</em> alt sitemizin bir <em>Ekip Sitesi</em> (<em>Team Site</em>) olacağını belirtiyor. Tüm site şablonları için <em>Get-SPWebTemplate</em> komutu kullanılabilir.</p>
<p style="text-align: justify;">Kolay gelsin...</p>
