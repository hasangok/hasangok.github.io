---
layout: post
title: WSS_Logging Veritabanının Aşırı Büyümesi
date: 2014-11-27 09:32
author: hasangok
comments: true
Tags: [Get-SPUsageDefinition, PowerShell, Sharepoint, SharePoint, Sharepoint 2013, WSS_Logging]
---
SharePoint loglarının saklandığı bu veritabanı, kullanımımıza göre çok hızlı sayılabilecek şekilde büyüyebiliyor. Normalde son 14 güne ait logların saklandığı bu veritabanını daha az veri saklayacak şekilde yapılandırabiliriz.
SharePoint farmında hangi aktivitelerin kaç günlük loglandığını öğrenmek için bir SharePoint 2013 Manahement Shell penceresi açıp şunu çalıştırabiliriz:

```powershell
Get-SPUsageDefinition
```
![Get-SPUsageDefinition-list](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/Get-SPUsageDefinition-list.png "Get-SPUsageDefinition-list")

Aşağıdaki PowerShell scriptini ***setRetentionDays.ps1*** adıyla kaydedip çalıştırırsanız, tüm aktivitelerin 3 gün loglanmasını sağlayabilirsiniz. Daha farklı bir değer için ise "**-day**" parametresi ile kaç gün olacağını belirterek çalıştırabiliriniz.

```powershell
.\setRetentionDays.ps1 -day 5
```
![Get-SPUsageDefinition](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/Get-SPUsageDefinition.png "Get-SPUsageDefinition")

***setRetentionDays.ps1***

```powershell
param(
[string]$day
)

Add-PSSnapin "Microsoft.SharePoint.PowerShell"

If($day -le 0)
 {
   $day = 3
 }

Write-Host "Changing retention values to $day days..."
$logCategories = Get-SPUsageDefinition

Foreach ($category in $logCategories)
{
	Set-SPUsageDefinition -Identity $category.Name -DaysRetained $day -erroraction 'silentlycontinue'
}

Write-Host "Completed!"
```