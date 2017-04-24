---
layout: post
title: SharePoint 2013 - The tool was unable to install Application Server Role, Web Server (IIS) Role
date: 2014-08-22 09:52
author: hasangok
comments: true
Tags: [preparation tool, SharePoint, Sharepoint 2013]
---
<p style="text-align: justify;">Bugün <em>Wndows Server 2012</em> üzerinde <em>SharePoint 2013</em> kurulumu yapmaya hazırlanırken <em>SharePoint 2013 Products Preparation Tool</em> başlıktaki hatayı verdi. Oldukça popüler bir hata olduğundan olsa gerek çeşit çeşit çözüm önerileri sunulmuş ve her bir öneri birilerinin hatasını gidermiş. Benim için çözüm olan yöntem ise şu şekildeydi:</p>

<ol style="text-align: justify;">
	<li>Başlat ekranına <em>MMC</em> yazıp çalıştırıyoruz.</li>
	<li><em>File</em> menüsünden <em>Add/Remove Snap-in</em> seçiyoruz.</li>
	<li><em>Group Policy Object Editor</em> seçip ekliyoruz.</li>
	<li><em>Computer Management</em> &gt; <em>Administrative Templates</em> &gt; <em>System</em> yolunu izliyoruz.</li>
	<li>"<em>Specify Settings for optional component installation and component repair</em>" seçiyoruz.</li>
	<li><em>Enable</em> seçip "<em>Contract Windows Update directly to download repair content instead of Windows Server Update Services (WSUS)</em>" önündeki checkbox'ı işaretliyoruz.</li>
</ol>
<p style="text-align: justify;">Bu adımları izledikten sonra Preparation Tool IIS'i kurup devam edebildi.</p>
<p style="text-align: justify;">İyi çalışmalar.</p>
