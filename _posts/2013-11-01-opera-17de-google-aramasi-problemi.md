---
layout: post
title: Opera 17'de Google Araması Problemi
date: 2013-11-01 14:18
author: hasangok
comments: true
Tags: [Google Arama, Opera, Opera 17, Programlar]
---
İş bilgisayarımı formatlayıp da *Opera*'yı tekrar yüklediğimde yaptığım tüm *Google* aramaları "**google.de**" üzerinden yapılıyordu. *Opera* arayüzünde konu ile ilgili herhangi bir ayar bulamadığımdan *Opera*'nın profil klasörü olan "*C:\Users\hasan.gok\AppData\Roaming\Opera Software\Opera Stable"* klasörüne göz atmak istedim. Evet, tahmin ettiğim gibi içeriği aşağıdaki gibi olan, "***Local State***" adlı bir dosya vardı:

```json
{
   "browserjs": {
      "version": "1381219435"
   },
   "hardware_acceleration_mode_previous": true,
   "intl": {
      "app_locale": "en-US"
   },
   "last_version": [ 17, 0, 1241, 53, 0 ],
   "location": {
      "country": "DE",
      "country_from_server": "DE",
      "timestamp": "1394934883600000000"
   },
   "sync": {
      "login_screen_reminder": 1
   },
   "update": {
      "components": {
         "next_check_interval": "28800"
      }
   }
}
```
Bu dosyayı *Not Defteri* ile açıp **DE** olarak gördüğümüz yerleri **TR** olarak değiştirdiğimizde aramalarımız **google.com.tr** üzerinden yapılmaya başlayacak.
