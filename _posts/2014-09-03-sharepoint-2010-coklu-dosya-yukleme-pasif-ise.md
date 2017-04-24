---
layout: post
title: SharePoint 2010 - Çoklu Dosya Yükleme Pasif İse
date: 2014-09-03 16:03
author: hasangok
comments: true
Tags: [Çoklu dosya yükleme, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><em>SharePoint 2010</em> kullanan bir müşterimizden, doküman kütüphanesine çoklu dosya yüklemek için yetki isteğini belirten bir mail aldım dün. Yetki ile alakalı bir durum olmadığını bilsem de daha önce detaylı araştırmadığım bir konu olduğundan kısaca buraya not etmek istedim. Çoklu dosya yükleme özelliği pasif ise, aşağıdaki maddeleri kontrol etmelisiniz:</p>

<ol style="text-align: justify;">
	<li>Çoklu dosya yükleyecek bilgisayarda <em>Microsoft Office</em> yüklü bulunmalı.</li>
	<li>İnternet Explorer'ın <strong>32-bit</strong> sürümünü kullanmalısınız.</li>
	<li>İnternet Explorer, <em>ActiveX</em> kontrollerinin çalışmasına izin vermeli.</li>
	<li>Görüntülediğiniz <em>SharePoint</em> sitesi güvenilen sitelere eklenmiş olmalı.</li>
	<li>İnternet Explorer'da "<strong>Korumalı Modu Etkinleştir</strong>" özelliği devre dışı olmalı.</li>
	<li><em>Central Administration</em> &gt; <em>Manage Web Applications</em> &gt; <em>Authentication Providers</em> &gt; <em>Client Integration</em> "Yes" olarak seçilmeli.</li>
	<li><em>Central Administration</em> &gt; <em>Manage Web Applications</em> &gt; <em>General Settings</em> &gt; <em>Enable additional actions and Online Status for members</em> "Yes" olarak seçilmeli.</li>
</ol>
<p style="text-align: justify;">Genel anlamda konuyla ilgili tüm öneriler bunlar olsa da muhtemelen kontrol ettiğiniz ilk birkaç maddede sorununuz çözülmüş olacaktır.</p>
