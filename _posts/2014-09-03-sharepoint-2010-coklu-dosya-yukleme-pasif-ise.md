---
title: SharePoint 2010 - Çoklu Dosya Yükleme Pasif İse
date: 2014-09-03 16:03
---

*SharePoint 2010* kullanan bir müşterimizden, doküman kütüphanesine çoklu dosya yüklemek için yetki isteğini belirten bir mail aldım dün. Yetki ile alakalı bir durum olmadığını bilsem de daha önce detaylı araştırmadığım bir konu olduğundan kısaca buraya not etmek istedim. Çoklu dosya yükleme özelliği pasif ise, aşağıdaki maddeleri kontrol etmelisiniz:

<!--more-->
1. Çoklu dosya yükleyecek bilgisayarda *Microsoft Office* yüklü bulunmalı.
2. İnternet Explorer'ın **32-bit** sürümünü kullanmalısınız.
3. İnternet Explorer, *ActiveX* kontrollerinin çalışmasına izin vermeli.
4. Görüntülediğiniz *SharePoint* sitesi güvenilen sitelere eklenmiş olmalı.
5. İnternet Explorer'da "**Korumalı Modu Etkinleştir**" özelliği devre dışı olmalı.
6. *Central Administration* &gt; *Manage Web Applications* &gt; *Authentication Providers* &gt; *Client Integration* "Yes" olarak seçilmeli.
7. *Central Administration* &gt; *Manage Web Applications* &gt; *General Settings* &gt; *Enable additional actions and Online Status for members* "Yes" olarak seçilmeli.

Genel anlamda konuyla ilgili tüm öneriler bunlar olsa da muhtemelen kontrol ettiğiniz ilk birkaç maddede sorununuz çözülmüş olacaktır.