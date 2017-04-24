---
layout: post
title: SharePoint SmallSearchInputBox Kontrolünü Özelleştirmek
date: 2014-03-17 10:00
author: hasangok
comments: true
Tags: [Search Service, Sharepoint, SharePoint, SmallSearchInputBox]
---
<p style="text-align: justify;"><em>SharePoint</em> arayüzünde bulunan bu küçük arama kutusunu, belirlediğimiz farklı bir arama sayfasını kullanması veya arama yapmadan önce scope seçimi yapılabilmesi için özelleştirmek isteyebiliyoruz. Bunu yapmak için <em>Visual Studio</em> ile <em>SmallSearchInputBox</em> kontrolünü override etmemiz mümkün. Yapmamız gereken <em>SharePoint</em> projemize, adı <em>SmallSearchInputBox</em> olan yeni bir <em>Empty Element</em> ekleyip, <strong>Elements.xml</strong> dosyasının içeriğini aşağıdakilerle değiştirmek:</p>

<pre class="lang:default decode:true">&lt;?xml version="1.0" encoding="utf-8"?&gt;
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
&lt;/Elements&gt;</pre>
<p style="text-align: justify;">Oluşturduğumuz bu kontrolü içerisine koyduğumuz özelliğin (<em>feature</em>) mutlaka <em><strong>Site</strong></em> scope'unda deploy edilmesi gerekiyor. Deploy ettikten sonra arama kutunuz değişmiyorsa, daha küçük <em>Sequence</em> değerleriyle tekrar deploy edip deneyebilirsiniz.</p>
<p style="text-align: justify;">İyi çalışmalar...</p>
