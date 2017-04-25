---
layout: post
title: SharePoint SmallSearchInputBox Kontrolünü Özelleştirmek
date: 2014-03-17 10:00
author: hasangok
comments: true
Tags: [Search Service, Sharepoint, SharePoint, SmallSearchInputBox]
---
*SharePoint* arayüzünde bulunan bu küçük arama kutusunu, belirlediğimiz farklı bir arama sayfasını kullanması veya arama yapmadan önce scope seçimi yapılabilmesi için özelleştirmek isteyebiliyoruz. Bunu yapmak için *Visual Studio* ile *SmallSearchInputBox* kontrolünü override etmemiz mümkün. Yapmamız gereken *SharePoint* projemize, adı *SmallSearchInputBox* olan yeni bir *Empty Element* ekleyip, **Elements.xml** dosyasının içeriğini aşağıdakilerle değiştirmek:

```html
&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;Elements xmlns="http://schemas.microsoft.com/sharepoint/"&gt;
  &lt;Control Id="SmallSearchInputBox"
       Sequence="25"
       ControlAssembly="Microsoft.SharePoint.Portal, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
       ControlClass="Microsoft.SharePoint.Portal.WebControls.SearchBoxEx"&gt;
    &lt;Property Name="DropDownMode"&gt;ShowDD&lt;/Property&gt;
    &lt;Property Name="SearchResultPageURL"&gt;/Arama/Sayfasi.aspx&lt;/Property&gt;
    &lt;Property Name="FrameType"&gt;None&lt;/Property&gt;
    &lt;Property Name="DropDownWidth"&gt;140&lt;/Property&gt;
    &lt;Property Name="TextBoxWidth"&gt;140&lt;/Property&gt;
    &lt;Property Name="ShowAdvancedSearch"&gt;true&lt;/Property&gt;
    &lt;Property Name="TextBeforeDropDown"&gt;Arama:&lt;/Property&gt;
    &lt;Property Name="AdvancedSearchPageURL"&gt;/Arama/Sayfasi.aspx&lt;/Property&gt;
    &lt;Property Name="QueryPromptString"&gt;Ara...&lt;/Property&gt;
  &lt;/Control&gt;
&lt;/Elements&gt;
```
Oluşturduğumuz bu kontrolü içerisine koyduğumuz özelliğin (*feature*) mutlaka ***Site*** scope'unda deploy edilmesi gerekiyor. Deploy ettikten sonra arama kutunuz değişmiyorsa, daha küçük *Sequence* değerleriyle tekrar deploy edip deneyebilirsiniz.
İyi çalışmalar...
