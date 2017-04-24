---
layout: post
title: Opera 17'de Google Araması Problemi
date: 2013-11-01 14:18
author: hasangok
comments: true
Tags: [Google Arama, Opera, Opera 17, Programlar]
---
<p style="text-align: justify;">İş bilgisayarımı formatlayıp da <em>Opera</em>'yı tekrar yüklediğimde yaptığım tüm <em>Google</em> aramaları "<strong>google.de</strong>" üzerinden yapılıyordu. <em>Opera</em> arayüzünde konu ile ilgili herhangi bir ayar bulamadığımdan <em>Opera</em>'nın profil klasörü olan "<em>C:\Users\hasan.gok\AppData\Roaming\Opera Software\Opera Stable"</em> klasörüne göz atmak istedim. Evet, tahmin ettiğim gibi içeriği aşağıdaki gibi olan, "<strong><em>Local State</em></strong>" adlı bir dosya vardı:</p>

<pre class="lang:default decode:true ">{
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
}</pre>
<p style="text-align: justify;">Bu dosyayı <em>Not Defteri</em> ile açıp <strong>DE</strong> olarak gördüğümüz yerleri <strong>TR</strong> olarak değiştirdiğimizde aramalarımız <strong>google.com.tr</strong> üzerinden yapılmaya başlayacak.</p>
