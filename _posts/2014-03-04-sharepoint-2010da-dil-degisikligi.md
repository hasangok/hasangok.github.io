---
layout: post
title: SharePoint 2010'da Dil Değişikliği
date: 2014-03-04 11:54
author: hasangok
comments: true
Tags: [Çoklu dil desteği, Dil Paketi, JavaScript, Sharepoint, SharePoint]
---
*SharePoint 2010* ile hazırladığımız çok dilli bir portalda, kullanıcıların dil değişikliklerini yapabilecekleri linkler bulunması gerekebiliyor. Türk bayrağına tıklayınca Türkçe'ye, İngiliz bayrağına tıklayınca İngilizce'ye geçmek için aşağıdaki scripti kullanmamız ve ilgili linklerin click fonksiyonlarını aşağıdaki şekilde yazmamız yeterli:

```javascript
function OnSelectionChange(value)
{ 
	var today = new Date();
	var oneYear = new Date(today.getTime() + 365 * 24 * 60 * 60 * 1000);
	var url = window.location.href;
	document.cookie = "lcid=" + value + ";path=/;expires=" + oneYear.toGMTString();
	window.location.href = url;
}
```
```html
&lt;a href="javascript:OnSelectionChange(1055)"&gt;Türkçe&lt;/a&gt;
&lt;a href="javascript:OnSelectionChange(1033)"&gt;English&lt;/a&gt;
```
İyi çalışmalar.