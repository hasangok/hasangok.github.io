---
layout: post
title: WSS_Logging Veritabanının Aşırı Büyümesi
date: 2014-11-27 09:32
author: hasangok
comments: true
Tags: [Get-SPUsageDefinition, PowerShell, Sharepoint, SharePoint, Sharepoint 2013, WSS_Logging]
---
<p style="text-align: justify;">SharePoint loglarının saklandığı bu veritabanı, kullanımımıza göre çok hızlı sayılabilecek şekilde büyüyebiliyor. Normalde son 14 güne ait logların saklandığı bu veritabanını daha az veri saklayacak şekilde yapılandırabiliriz.</p>
<p style="text-align: justify;">SharePoint farmında hangi aktivitelerin kaç günlük loglandığını öğrenmek için bir SharePoint 2013 Manahement Shell penceresi açıp şunu çalıştırabiliriz:</p>

<pre class="lang:default decode:true   ">Get-SPUsageDefinition</pre>
<!--more-->
<p style="text-align: justify;"><a href="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/Get-SPUsageDefinition-list.png"><img class="alignnone wp-image-778 size-full" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/Get-SPUsageDefinition-list.png" alt="Get-SPUsageDefinition-list" width="475" height="342" /></a></p>
<p style="text-align: justify;">Aşağıdaki PowerShell scriptini <em><strong>setRetentionDays.ps1</strong></em> adıyla kaydedip çalıştırırsanız, tüm aktivitelerin 3 gün loglanmasını sağlayabilirsiniz. Daha farklı bir değer için ise "<strong>-day</strong>" parametresi ile kaç gün olacağını belirterek çalıştırabiliriniz.</p>

<pre class="lang:default decode:true ">.\setRetentionDays.ps1 -day 5</pre>
<p style="text-align: justify;"><img class="alignnone wp-image-774 size-full" src="https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/11/Get-SPUsageDefinition.png" alt="Get-SPUsageDefinition" width="480" height="84" /></p>
<p style="text-align: justify;"><em><strong>setRetentionDays.ps1</strong></em></p>

<pre class="lang:default decode:true" title="setRetentionDays.ps1">param(
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

Write-Host "Completed!"</pre>
