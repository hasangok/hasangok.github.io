---
layout: post
title: PowerShell - Correlation ID ile Hata Ayrıntılarını Görmek
date: 2014-07-05 09:00
author: hasangok
comments: true
Tags: [Correlation ID, PowerShell, PowerShell, Sharepoint, SharePoint, Sharepoint 2013]
---
<p style="text-align: justify;">SharePoint ile tanıştığım günden beri sayısız kez karşılaştığım ekran budur sanırım: "<em>Sorry, something went wrong</em>". Bu hatayı bir Correlation ID ile bize gösteren SharePoint, hata detaylarını log dosyalarında saklıyor bildiğimiz gibi. Log dosyalarında bu ID'yi arayarak hata detaylarını bulmaya çalışmak yerine, aşağıdaki satırları <em>PowerShell</em>'de çalıştırmak bize ilgili hatanın detaylarını getirecektir.</p>

<pre class="lang:default decode:true">get-splogevent | ?{$_.Correlation -eq "&lt;Correlation ID&gt;"} | select Area, Category, Level, EventID, Message</pre>
<p style="text-align: justify;"><img class="aligncenter size-full wp-image-717" src="http://www.hasangok.com.tr/wp-content/uploads/2014/07/retrieve-log-by-correlation-id.png" alt="retrieve-log-by-correlation-id" width="677" height="343" />Aşağıdaki gibi bir ekleme yaparak C:\hata.txt dosyasına bu detayları kaydetmek de isteyebilirsiniz.</p>

<pre class="lang:default decode:true ">get-splogevent | ?{$_.Correlation -eq "&lt;Correlation ID&gt;"} | select Area, Category, Level, EventID, Message | Format-List &gt; C:\hata.txt</pre>
Hata ayıklamada hepinize başarılar :)
Görüşmek üzere...
