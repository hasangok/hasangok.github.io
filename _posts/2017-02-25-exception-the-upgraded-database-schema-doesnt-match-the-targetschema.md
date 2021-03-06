---
layout: post
title: Exception - The upgraded database schema doesn't match the TargetSchema
date: 2017-02-25 21:33
author: hasangok
comments: true
Tags: [SharePoint, SharePoint 2016, SharePoint Management Shell]
---
Uzun bir aradan sonra tekrar merhaba. Yeni bir yazı, yeni bir problem ile tekrar sizlerleyim.

Yeni kurduğumuz SharePoint 2016 Farm'ına yüklediğimiz patchler sonrası upgrade ederken Configuration Wizard sürekli hata alıyordu. İlgili log dosyalarını incelediğimde (Central Administration &gt; Upgrade and Migration &gt; Check upgrade status yolunda Failed olan satırlarda log dosyası adreslerini görebiliyoruz) gördüm ki aşağıdaki hatayı alıyoruz:
```
Upgrade [SPContentDatabase Name=WSS_Content] failed.
Exception: The upgraded database schema doesn't match the TargetSchema
     at Microsoft.SharePoint.Upgrade.SPDatabaseWssSequence.Upgrade()
     at Microsoft.SharePoint.Upgrade.SPUpgradeSession.RunUpgraders(Object o, List`1 lstClass)
     at Microsoft.SharePoint.Upgrade.SPUpgradeSession.Upgrade(Object o, Boolean bRecurse)
```
<!--more-->
Bunun için öncelikle content database'leri upgrade etmemiz, sonrasında Configuration Wizard'ı çalıştırmamız gerekiyor. SharePoint 2016 Management Shell açarak aşağıdaki satırı çalıştırmak yeterli olacak:
```powershell
Get-SPContentDatabase | ?{$_.NeedsUpgrade -eq $true} | Upgrade-SPContentDatabase -Confirm:$false
```
Sonrasında Configuration Wizard başarılı bir şekilde tamamlanacak. Check Upgrade Status sayfasından da başarıyla tamamlandığını görebilirsiniz.

Kolaylıklar...
