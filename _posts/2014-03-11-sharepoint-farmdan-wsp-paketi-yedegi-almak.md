---
layout: post
title: SharePoint Farm'dan WSP Paketi Yedeği Almak
date: 2014-03-11 13:49
author: hasangok
comments: true
Tags: [PowerShell, Sharepoint, SharePoint, Sharepoint 2013, wsp]
---
<p style="text-align: justify;">Arkadaşımız <a href="http://www.sdemir.com" target="_blank">Selçuk</a>'un paylaştığı faydalı bilgiyi aktarmak istedim:</p>
<p style="text-align: justify;">Bazen canlı ortamda wsp paketini güncellemeden önce, mevcut çalışan wsp paketimizin yedeğini almak isteyebiliriz. Bu aşağıdaki bir kaç satırlık kodla bunu yapabiliriz.</p>

<pre class="lang:default decode:true">$farm = Get-SPFarm
$file = $farm.Solutions.Item("SharePointSolution.wsp").SolutionFile
$file.SaveAs("c:\SharePointSolution.wsp")</pre>
<p style="text-align: justify;">İyi çalışmalar...</p>
