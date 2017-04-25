---
layout: post
title: PowerShell - Correlation ID ile Hata Ayrıntılarını Görmek
date: 2014-07-05 09:00
author: hasangok
comments: true
Tags: [Correlation ID, PowerShell, PowerShell, Sharepoint, SharePoint, Sharepoint 2013]
---
SharePoint ile tanıştığım günden beri sayısız kez karşılaştığım ekran budur sanırım: "*Sorry, something went wrong*". Bu hatayı bir Correlation ID ile bize gösteren SharePoint, hata detaylarını log dosyalarında saklıyor bildiğimiz gibi. Log dosyalarında bu ID'yi arayarak hata detaylarını bulmaya çalışmak yerine, aşağıdaki satırları *PowerShell*'de çalıştırmak bize ilgili hatanın detaylarını getirecektir.

```powershell
get-splogevent | ?{$_.Correlation -eq "&lt;Correlation ID&gt;"} | select Area, Category, Level, EventID, Message
```
![retrieve-log-by-correlation-id](https://raw.githubusercontent.com/hasangok/hasangok.github.io/master/uploads/2014/07/retrieve-log-by-correlation-id.png "retrieve-log-by-correlation-id")

Aşağıdaki gibi bir ekleme yaparak *C:\hata.txt* dosyasına bu detayları kaydetmek de isteyebilirsiniz.

```powershell
get-splogevent | ?{$_.Correlation -eq "&lt;Correlation ID&gt;"} | select Area, Category, Level, EventID, Message | Format-List &gt; C:\hata.txt
```

Hata ayıklamada hepinize başarılar :)
Görüşmek üzere...
