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
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
  <Control Id="SmallSearchInputBox"
       Sequence="25"
       ControlAssembly="Microsoft.SharePoint.Portal, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
       ControlClass="Microsoft.SharePoint.Portal.WebControls.SearchBoxEx">
    <Property Name="DropDownMode">ShowDD</Property>
    <Property Name="SearchResultPageURL">/Arama/Sayfasi.aspx</Property>
    <Property Name="FrameType">None</Property>
    <Property Name="DropDownWidth">140</Property>
    <Property Name="TextBoxWidth">140</Property>
    <Property Name="ShowAdvancedSearch">true</Property>
    <Property Name="TextBeforeDropDown">Arama:</Property>
    <Property Name="AdvancedSearchPageURL">/Arama/Sayfasi.aspx</Property>
    <Property Name="QueryPromptString">Ara...</Property>
  </Control>
</Elements>
```
Oluşturduğumuz bu kontrolü içerisine koyduğumuz özelliğin (*feature*) mutlaka ***Site*** scope'unda deploy edilmesi gerekiyor. Deploy ettikten sonra arama kutunuz değişmiyorsa, daha küçük *Sequence* değerleriyle tekrar deploy edip deneyebilirsiniz.
İyi çalışmalar...
