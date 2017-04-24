---
layout: post
title: SharePoint 2010'da Dil Değişikliği
date: 2014-03-04 11:54
author: hasangok
comments: true
Tags: [Çoklu dil desteği, Dil Paketi, JavaScript, Sharepoint, SharePoint]
---
<p style="text-align: justify;"><em>SharePoint 2010</em> ile hazırladığımız çok dilli bir portalda, kullanıcıların dil değişikliklerini yapabilecekleri linkler bulunması gerekebiliyor. Türk bayrağına tıklayınca Türkçe'ye, İngiliz bayrağına tıklayınca İngilizce'ye geçmek için aşağıdaki scripti kullanmamız ve ilgili linklerin click fonksiyonlarını aşağıdaki şekilde yazmamız yeterli:</p>

<pre class="lang:js decode:true">&lt;script type ="text/javascript"&gt; 
function OnSelectionChange(value)
{ 
var today = new Date();
var oneYear = new Date(today.getTime() + 365 * 24 * 60 * 60 * 1000);
var url = window.location.href;
document.cookie = "lcid=" + value + ";path=/;expires=" + oneYear.toGMTString();
window.location.href = url;
}
&lt;/script&gt;</pre>
<pre class="lang:default decode:true">&lt;a href="javascript:OnSelectionChange(1055)"&gt;Türkçe&lt;/a&gt;
&lt;a href="javascript:OnSelectionChange(1033)"&gt;English&lt;/a&gt;</pre>
İyi çalışmalar.
