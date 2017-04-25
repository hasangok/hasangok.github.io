---
layout: post
title: SharePoint Farm'dan WSP Paketi Yedeği Almak
date: 2014-03-11 13:49
author: hasangok
comments: true
Tags: [PowerShell, Sharepoint, SharePoint, Sharepoint 2013, wsp]
---
Arkadaşımız [Selçuk](http://www.sdemir.com)'un paylaştığı faydalı bilgiyi aktarmak istedim:
Bazen canlı ortamda wsp paketini güncellemeden önce, mevcut çalışan wsp paketimizin yedeğini almak isteyebiliriz. Bu aşağıdaki bir kaç satırlık kodla bunu yapabiliriz.

```powershell
$farm = Get-SPFarm
$file = $farm.Solutions.Item("SharePointSolution.wsp").SolutionFile
$file.SaveAs("c:\SharePointSolution.wsp")
```
İyi çalışmalar...
